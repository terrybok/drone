

## Setup

### Launch sitl with docker (recommended option)

To instead launch sitl using docker

1. [Install docker](https://docs.docker.com/engine/install/ubuntu/), [nvidia-docker](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html) and [docker compose](https://docs.docker.com/compose/)

2. Update

```bash
sudo apt-get update
```

3. Clone the repository

```bash
git clone https://github.com/tilties2/PX4-OmniQuad.git
```

4. Initialize submodules

```bash
cd PX4-Omniquad
git submodule update --init --recursive
```

5. Go inside docker folder

```bash
cd PX4-OmniQuad/Docker
```

6. Build docker image

```bash
docker compose build omniquad-sitl
```

7. Create docker container and launch it

```bash
docker compose up -d omniquad-sitl
```

8. Create a terminal inside docker container

```bash
docker exec -it omniquad-sitl-cnt zsh
```

9. Build and launch sitl

```bash
make px4_sitl gazebo-classic_omniquad
```

### Launch sitl (without docker)

Further information regards PX4 Software-In-The-Loop can be found at the official website [Simulation](https://docs.px4.io/v1.14/en/simulation/)

1. Clone the repository

```bash
git clone https://github.com/tilties2/PX4-OmniQuad.git
```

2. Initialize submodules

```bash
cd PX4-Omniquad
git submodule update --init --recursive
```

3. Install dependencies

```bash
cd PX4-OmniQuad/Tools/setup
./ubuntu.sh
```

4. Build and launch sitl

```bash
cd PX4-OmniQuad
make px4_sitl gazebo-classic_omniquad
```

### Connect with ROS2 with docker

Further information on ROS2 with PX4 can be found here [ROS 2 User Guide ](http://docs.px4.io/main/en/ros2/user_guide)

1. Open new terminal inside the container

```bash
docker exec -it omniquad-sitl-cnt zsh
```

2. Start the agent and connect with ROS2

```bash
MicroXRCEAgent udp4 -p 8888
```
