# Kicktipp-Bot

This script can automatically enter tips into Kicktipp based on the quotes of the bookmakers. It is written in Python and uses Selenium to interact with the website.

## Easy Install

Execute the commands below in the `Terminal`-Program:

```bash
# Install brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Docker
brew install docker

# Get Image
docker pull antonengelhardt/kicktipp-bot

# Run Container and set your env variables
docker run -it --name kicktipp-bot -e KICKTIPP_EMAIL=<YOUR_EMAIL> -e KICKTIPP_PASSWORD=<YOUR_PASSWORD> -e KICKTIPP_NAME_OF_COMPETITION=<NAME_OF_COMPETITION> antonengelhardt/kicktipp-bot
```

## Setup when running without Docker

1. Clone the repository

2. Install chromedriver (<https://chromedriver.chromium.org/downloads>)

    Please choose the version that corresponds to your Chrome version.

3. Install the requirements

    ```bash
    pip3 install -r requirements.txt
    ```

4. Set the constant `CHROMEDRIVER_PATH` to the path of the chromedriver executable.

    It is recommended to place the executable in the same directory as the script or into the Applications folder.

5. Set the constants `EMAIL`, `PASSWORD` and `NAME_OF_COMPETITON` as environment variables to your Kicktipp credentials to the day on which the script should be executed. 0 corresponds to Sunday and 6 to Saturday. It is recommended to set it to 3 (Wednesday) or 4 (Thursday).

    For zsh:

    ```bash
    echo 'export KICKTIPP_EMAIL=<KICKTIPP_EMAIL>' >> ~/.zshenv  
    echo 'export KICKTIPP_PASSWORD=<KICKTIPP_PASSWORD>' >> ~/.zshenv   
    echo 'export KICKTIPP_NAME_OF_COMPETITION=<NAME_OF_COMPETITION>' >> ~/.zshenv
    ```

    For bash:

    ```bash
    echo 'export KICKTIPP_EMAIL=<KICKTIPP_EMAIL>' >> ~/.bash_profile      
    echo 'export KICKTIPP_PASSWORD=<KICKTIPP_PASSWORD>' >> ~/.bash_profile  
    echo 'export KICKTIPP_NAME_OF_COMPETITION=<NAME_OF_COMPETITION>' >> ~/.bash_profile
    ```

6. Select the driver you need by commenting out the unneeded driver in the `main` function.

7. Execute the script

    ```python3 main.py```

## Setup when running with Docker

1. Clone the repository

2. Install Docker (<https://docs.docker.com/get-docker/>)

3. Pull the image from Docker Hub or build it yourself

    ```bash
    docker pull antonengelhardt/kicktipp-bot

    # or 

    docker build -t antonengelhardt/kicktipp-bot .
    ```

4. Select the driver you need by commenting out the unneeded driver in the `main` function.

5. Run the container in the foreground

    ```bash
    docker run -it --name kicktipp-bot -e KICKTIPP_EMAIL=<YOUR_EMAIL> -e KICKTIPP_PASSWORD=<YOUR_PASSWORD> -e KICKTIPP_NAME_OF_COMPETITION=<NAME_OF_COMPETITION> antonengelhardt/kicktipp-bot
    ```

6. Run the container in the background

    ```bash
    docker run -d --name kicktipp-bot -e KICKTIPP_EMAIL=<YOUR_EMAIL> -e KICKTIPP_PASSWORD=<YOUR_PASSWORD> -e KICKTIPP_NAME_OF_COMPETITION=<NAME_OF_COMPETITION> antonengelhardt/kicktipp-bot
    ```

### Check logs

```bash
docker logs kicktipp-bot
```

### Stop container

```bash
docker stop kicktipp-bot
```

### Start container

```bash
docker start kicktipp-bot
```

### Remove container

```bash
docker rm kicktipp-bot
```
