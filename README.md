# Docker Useful commands

- List all the running docker container
        
        docker ps  
- List all the running docker container ID
        
        docker ps -aq
- List all the images 

        docker images ls
- List all the containers

        docker container ls
- Run docker container in a detached mode 

        docker run -d [image]:version/tag   
        docker run -d ngnix:latest
- Running docker container in a detached mode with exposing port

        docker run -d -p host_port:contianer_port [image]:version/tag   
        docker run -d -p 8080:80 ngnix:latest
- Stopping running docker container

        docker stop [container_id]
- Running docker container in a detached mode with exposing multiple ports

        docker run -d -p host_port:contianer_port -p host_port:contianer_port [image]:version/tag   
        docker run -d -p 8080:80 -p 3000:80 ngnix:latest
- Removing docker container

        docker rm [container_id]
    Note : docker rm will not remove running container, To stop running instance try with flag -f(force),

        docker rm -f [container_id]
        docker rm -f $(docker ps -aq)

        Second command will remove all the existing docker container by filtering container_ids
- Creating a docker container with custom name

        docker run --name custom_name -d host_port:contianer_port [image]:version/tag  

        docker run --name website -d 8080:80 ngnix:latest

- Displaying results with formatted style(docker-ps-vertical)
    
        export FORMAT="ID\t{{.ID}}\nNAME\t{{.Names}}\nIMAGE\t{{.Image}}\nPORTS\t{{.Ports}}\nCOMMAND\t{{.Command}}\nCREATED\t{{.CreatedAt}}\nSTATUS\t{{.Status}}\n"

        docker ps --format = $FORMAT
- Pushing our custom html file directly to nginx server

        docker run --name custom_containername -v Source_html_path:Destination_HTML_path:mode -p host_port:contianer_port [image]:version/tag 

        docker run --name website -v $(pwd):/usr/share/nginx/html:ro -p 8080:80 ngnix:latest

        mode = ro
        ro - only read

- Executing in a interaction mode in bash

        docker exec -it container-name bash
        docker exec -it website bash
- Exitting from bash interaction mode 

        exit

- Creating a new container from the mounted volume

        docker run --name container_name --voulme-from container_name -d  -p host_port:contianer_port [image]:version/tag 
- Login in to external docker container
    
        docker login servername
- Inspecting container id 

        docker inspect container_id 

- Logging container_id

        docker logs container_id

- creating dockerfile

        touch Dockerfile

- Building custom docker image 

        docker build --tag website:latest
- Pulling docker image of node-alpine

        docker pull node:alpine 
- Setting up the tag for our cusotm build image from present to future tag, which overwrite container name

        docker tag [tag_name_present]:version [tag_name_future]:version
- Removing one or more images of docker

        docker rmi [option] image:tag



        


