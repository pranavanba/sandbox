# sandbox

Use Docker as sandbox environments for running and testing commands, code, programs, logs, etc. in various languages

# Requirements

**Install Docker**: If you don't have Docker installed already, you can download and install it from the official Docker website (https://www.docker.com). Choose the appropriate version for your operating system and follow the installation instructions.

# Usage

1. **Create a Dockerfile**: Create a text file named **`Dockerfile`** (without any file extension) in an empty directory. If you are using multiple **`Dockerfile`** files, create each **`Dockerfile`** in a different directory. This file will define the configuration for your Docker container.

2. **Add your instructions and commands**: Adjust the **`Dockerfile`** contents according to your specific use case and requirements.

3. **Build the Docker image**: Open a terminal or command prompt, navigate to the directory containing the **`Dockerfile`**, and run the following command to build the Docker image:

```bash
docker build -t my-sandbox .
```

The **`-t`** option assigns a tag (in this case, **`my-sandbox`**) to the Docker image, allowing you to reference it easily. The **`.`** (dot) option in the docker build command represents the current directory as the build context. It includes the files and directories from the current directory in the build process, allowing Docker to access and incorporate them into the Docker image being built.

4. **Run the Docker container**: Once the image is built, you can run it as a container using the following command:

```bash
docker run --rm my-sandbox
```

The **`--rm`** option ensures that the container is automatically removed after it finishes running.

The instructions and commands you specified in your **`Dockerfile`** will now execute within the Docker container, isolated from your local environment. Any changes made or dependencies installed within the container will not affect your host machine.

Remember to clean up any temporary containers or images after you're done testing by running the **`docker rm <container-id>`** and **`docker rmi <image-id>`** commands, respectively.

# Useful Docker commands 

**Check exposed ports for all containers**

```bash
docker ps -a --format "table {{.Names}}\t{{.Ports}}"
```

**Check containers**

```bash
docker ps -a
```

**Making changes to a docker container where you need to rebuild the image**

| Command | Explanation |
---|---
| `docker stop <container-name>` | Stops a running container with the specified name. |
| `docker rm <container-name>` | Removes a stopped container with the specified name. |
| `docker rmi <image-name>` | Removes an image with the specified name. |
| `docker build --no-cache...` | Builds a Docker image with the `--no-cache` option, which prevents using cached layers during the build process. This ensures that each build step is executed freshly. |
| `docker image prune` | Removes unused images from the local Docker image cache, freeing up disk space. |
| `docker run...` | Runs a Docker container based on a specified image, with various options such as port mapping, environment variables, and more. |
