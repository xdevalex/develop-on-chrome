# Dev on a pixelbook using docker and vscode

## Enabling the Linux beta

Go into settings, search for Linux and then enable the Linux beta. this will allow you to launch the terminal app.

## Installing Docker

Follow the steps to install Docker Community Edition (CE) for linux. As linux for ChromeOS is running debian I followed the instructions for the latest version of that.

### SET UP THE REPOSITORY

Update the apt package index:

`sudo apt update`

Install packages to allow apt to use a repository over HTTPS:

```
sudo apt install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

Add Docker’s official GPG key:

`curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -`

Use the following command to set up the stable repository.

```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
```

### INSTALL DOCKER CE

Update the apt package index.

`sudo apt update`

Install the latest version of Docker CE, or go to the next step to install a specific version:

`sudo apt install docker-ce`

The Docker daemon starts automatically.

Verify that Docker CE is installed correctly by running the hello-world image.

`sudo docker container run hello-world`

This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.

If you would like to use Docker as a non-root user, you should now consider adding your user to the “docker” group with something like:

`sudo usermod -aG docker $USER`


Remember to log out and back in for this to take effect!


## Installing docker-compose

Run this command to download the latest version of Docker Compose:

`sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

Apply executable permissions to the binary:

`sudo chmod +x /usr/local/bin/docker-compose`

## Installing vscode

Go to https://code.visualstudio.com and download the latest .deb

Install the deb directly (note the leading `./` which tells apt it isn’t a package name

`sudo apt install ./<file>.deb`

Then update the package cache and install the package using:

```
sudo apt install apt-transport-https
sudo apt update
sudo apt install code
```

Seeing it in action

Make sure the linux terminal is running, clone your repository, cd into that working directory and launch `code`.

From there I can run the embedded terminal and issue `docker-compose up` etc commands.

Then open a browser and navigate to the `localhost:8000` or whichever exposed ports your app has.
