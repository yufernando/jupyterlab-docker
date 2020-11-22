# JupyterLab Docker

This is the repository of my custom JupyterLab Docker image. 

Specs:

- Vim Keybindings.
- Variable inspector.
- Jupyterlab-git extension.
- Material Darker Theme
- Jupyterlab Table of Contents.
- NBDime for easy diffing Jupyter Notebooks.

## Build the Docker image

```
git clone git@github.com/yufernando/jupyterlab-docker
cd jupyterlab-docker
docker build -t yufernando/jupyterlab-vim .
```

### (Optional) Push to Docker Hub

```
docker push yufernando/jupyterlab-vim
```

## Run the Docker container

Run the image created in the first above:
```
docker run --rm -p 8888:8888 -v $PWD:/home/jovyan/work -e JUPYTER_ENABLE_LAB=yes jupyterlab-vim
```

Or run an image from Docker Hub:
```
docker run --rm -p 8888:8888 -v $PWD:/home/jovyan/work -e JUPYTER_ENABLE_LAB=yes yufernando/jupyterlab-vim
```

## Using docker-compose

The docker-compose script mounts a volume from the host folder `notebooks`.

Clone the repository:

`git clone https://github.com/yufernando/jupyterlab-docker`

Start the Docker container

`docker-compose up`

Remove the container:

`docker-compose down`

## Using make

You can simplify the workflow above using `make`. 

You can build the image by running:
```
make build
```

This will create an image with two tags: the latest commit hash and "latest".

Then push the image with both tags to Docker Hub:

```
make push
```
