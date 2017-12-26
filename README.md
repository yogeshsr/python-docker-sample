## Hands-on

1. Create a dockerised app
2. Build the app to create docker image
3. Publish the image
4. Run the image standalone
5. Create VM machines
6. Deploy app stack to swarm cluster


## Dockerfile
Defination of the container which is pushed as yogeshsr/get-started:part2
This adds the app.py at build. Change to app.py needs rebuild of image.
Alternatively, mount a folder for code as mentioned in Docker compose product manual.
https://docs.docker.com/get-started/part2/

## Standalone
See this how to link redis container with app container, when both are standalone container
https://docs.docker.com/samples/library/redis/


## docker-compose-standalone.yaml
use above file along with docker-compose
https://docs.docker.com/compose/gettingstarted/

## docker-compose.yaml
Use above file to setup swarm cluster
Note that the redis will be using mounted host (myvm1) /home/redis/data folder
https://docs.docker.com/get-started/part4/


## Notes

Use docker-compose to create services which defines num of containers to run, load-balance, etc

Create swarm cluster and deploy the app in docker cluster. docker-machine is used to create VMs to add nodes to the custer. Each vm will be running 1 or more containers. use docker stack deploy the services.


Compose is a tool for defining and running multi-container Docker applications.
* container is defined by Dockerfile

For prod, deploy to swarm cluster using compose
To rebuild if local app code, use compose build
setup remote(s) m/c using docker-machine,setup swarm for multiple hosts, or use docker-compose over single remote m/c

Compose has commands for managing the whole lifecycle of your application:

Start, stop, and rebuild services
View the status of running services
Stream the log output of running services
Run a one-off command on a service

docker-compose up | install service to the container
#-d detached mode
docker-compose ps
docker-compose down --volumes


To deploy serice stack to swarm
swarm support deploy, replicas
create m/c using docker-machine
docker-machine ls
docker-machine ssh myvm1 #or
docker-machine env myvm1 #and set the shell by running last command dispalyed

run the below over the swarm mgr node
docker swarm init
docker stack deploy
docker service ls


## Commands

docker info

ps -ef | grep docker

ps -ef | grep elastic

ps -eo pid,comm,cmd | grep elastic

ps -eo pid,comm | grep elastic

ps -eo pid,comm | grep docker

ps -eo pid,comm,cmd,cgroup | grep docker

ls /usr/share/elasticsearch/config

docker info

ps -eo pid,comm,cmd,cgroup | grep docker

ps -eo pid,comm,cmd,cgroup | grep elastic

docker images

docker images

lsof -i :4000

lsof -i:4000

ps aux | grep 808

docker container ls

docker image ls -a

docker stack ls

## All commands


mkdir elastic

cd el

cd elastic/

touch docker-compose.yml

subl .

tail docker-compose.yml 

docker-compose up

ls

docker --version

docker-compose --version

docker-machine --version

docker ps

docker run hello-world

ls

docker ps -a

docker images

pwd

docker --version

env | grep DOCKER

docker-compose up

docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:6.1.1

cd ../

ls

mkdir python-docker-sample

cd $!

pwd

cd -

cd python-docker-sample/

touch requirements.txt

echo "Flask\nRedis"

printf "Flask\nRedis"

echo -e "Flask\nRedis"

echo -e "Flask\nRedis" > requirements.txt 

cat requirements.txt 

touch app.py

subl .

touch Dockerfile

subl .

lof 80

lsof -i :80

ls

docker build -t friendlyhello .

docker build -t friendlyhello .

docker run -p 4000:80 friendlyhello

touch docker-compose.yml

docker login

docker tag friendlyhello yogeshsr/get-started:part2

docker push yogeshsr/get-started:part2

docker run -p 4000:80 yogeshsr/get-started:part2

docker swarm init

docker stack deploy -c docker-compose.yml getstartedlab

docker service ls

docker service ps getstartedlab_web 

docker container ls -q

docker stack rm getstartedlab

docker swarm leave --force

docker-machine ls

docker-machine create --driver virtualbox myvm1

docker-machine create --driver virtualbox myvm2

docker stask ls

docker container ls

docker-machine ls

docker swarm init

docker swarm leave --force

docker-machine ssh myvm1 "docker swarm init --advertise-addr 192.168.99.100"

docker-machine ls

docker-machine ssh myvm2 "docker swarm join --token SWMTKN-1-0agf7dh0ypfqmbqhn2sie4xwi0dlkduempgvwjupov9imyu0sq-6lyizpapmai5i8t76pjfuvi5k 192.168.99.100:2377"

docker-machine ssh myvm1 "docker node ls"

docker-machine ls -q

docker-machine ls

docker-machine env myvm1

eval $(docker-machine env myvm1)

docker-machine ls

pwd

ls

docker stack deploy -c docker-compose.yml getstartedlab

docker stack ps getstartedlab

docker-machine ls

lsof :80

lsof -i:80

docker-machine ls

docker stack rm getstartedlab && docker swarm leave --force

docker service ps getstartedlab

docker-machine ls

docker stack rm getstartedlab

eval $(docker-machine env -u)

docker-machine ls

docker-machine env myvm1

eval $(docker-machine env myvm1)

docker-machine ls

docker stack deploy -c docker-compose.yml getstartedlab

docker stack deploy -c docker-compose.yml getstartedlab

docker stack ls

docker-machine ls

docker-machine ssh myvm1 "docker swarm init --advertise-addr 192.168.99.100"

docker-machine ssh myvm2 "docker swarm join --token SWMTKN-1-41970him35i7jyfo2x721clsgyidmqpngnhqmcwh46cde3ie3f-94ce9a2xz4qixo5nr2iu5xdag 192.168.99.100:2377"

docker-machine env

docker-machine env myvm2

eval $(docker-machine env myvm2)

docker stack ps getstartedlab

docker-machine ssh myvm2 "docker swarm join --token SWMTKN-1-41970him35i7jyfo2x721clsgyidmqpngnhqmcwh46cde3ie3f-94ce9a2xz4qixo5nr2iu5xdag 192.168.99.100:2377"

docker stack ps getstartedlab

docker-machine env myvm1

eval $(docker-machine env myvm1)

docker stack ps getstartedlab

docker stack deploy -c docker-compose.yml getstartedlab

docker-machine env myvm1

docker node ls

docker-machine ssh myvm2 "docker swarm join --token SWMTKN-1-41970him35i7jyfo2x721clsgyidmqpngnhqmcwh46cde3ie3f-94ce9a2xz4qixo5nr2iu5xdag 192.168.99.100:2377"

docker-machine ssh myvm2 "docker swarm leave"

docker-machine ssh myvm2 "docker swarm join --token SWMTKN-1-41970him35i7jyfo2x721clsgyidmqpngnhqmcwh46cde3ie3f-94ce9a2xz4qixo5nr2iu5xdag 192.168.99.100:2377"

docker stack deploy -c docker-compose.yml getstartedlab

docker stack rm getstartedlab

eval $(docker-machine env -u)

docker-machine ls

docker-machine ssh myvm2 "docker swarm leave

docker-machine ssh myvm2 "docker swarm leave"

docker-machine ssh myvm1 "docker swarm leave --force"

docker-machine ls

docker stack rm getstartedlab

docker-machine ls

docker-machine ssh myvm1 "docker swarm init --advertise-addr 192.168.99.100"

docker-machine ssh myvm2 "docker swarm join --token SWMTKN-1-615sjpomlius58n8kujmjfty8xdszdajv67iztpavyupd8lyab-bbckelhpozlqgnvyfyc33nwuv 192.168.99.100:2377"

docker-machine ssh myvm1 "docker node ls"

docker-machine env myvm1

eval $(docker-machine env myvm1)

docker stack deploy -c docker-compose.yml getstartedlab

docker stack ps getstartedlab

docker stack ps getstartedlab

docker-machine ssh myvm1 "mkdir ./data"

docker stack deploy -c docker-compose.yml getstartedlab

docker service ls

docker stack ps getstartedlab

docker stack rm getstartedlab

docker stack ps getstartedlab





