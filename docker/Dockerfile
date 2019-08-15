# REFERENCE: https://tsaprailis.com/2017/10/10/Docker-for-data-science-part-1-building-jupyter-container/

# Use the latest ubuntu image as base for the new image
# ubuntu is the image name and latest is a tag that 
# references a particular version of the image.
# In this case latest is always the latest LTS image
# at the time of writing this, it's 16.04.
FROM ubuntu:latest

# Run a system update to get it up to speed
# Then install python3 and pip3
RUN apt-get update && apt-get install -y python3 \
    python3-pip

# Install jupyter
RUN pip3 install jupyter
# Install nbinteract
RUN pip3 install nbinteract
# Install cmake required by compute-rhino3d
RUN pip3 install cmake
# Install compute-rhino3d
RUN pip3 install compute-rhino3d

# Create a new system user
RUN useradd -ms /bin/bash jupyter

RUN mkdir /notebooks

# Change to this new user
USER jupyter

# RUN chown jupyter /notebooks

# Set the container working directory to the user home folder
WORKDIR /notebooks


# Start the jupyter notebook
ENTRYPOINT ["jupyter", "notebook", "--ip=*"]

# RUN pip install pip --upgrade
# ADD requirements.txt /code
# RUN pip install -r requirements.txt
# RUN mkdir /notebooks
# CMD jupyter notebook --no-browser --ip 0.0.0.0 --port 8888 /notebooks