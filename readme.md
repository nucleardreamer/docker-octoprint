# Dockrized octoprint

This container includes the following programs, and are all located in `/opt`. Here is the file directory list:

```
/config
  └── config.yaml
/opt
  ├── octoprint/
  ├── cura/
  ├── slic3r/
  ├── mjpg-streamer/
  └── ffmpeg/
```

## Control

If you want to restart any service, you can issue a command right into the container. Examples:

* Restart the octoprint server
  ```
  $ docker exec -t octoprint supervisorctl restart printer:octoprint
  ```
* Restart the mjpeg-stream server
  ```
  $ docker exec -t octoprint supervisorctl restart printer:mjpeg
  ```
* See all services running interactively
  ```
  $ docker exec -it octoprint supervisorctl
  ```

## Config

By default, the configuration without any volume mount has no access control or connectivity checking. The base octoprint config directory is located in `/config`, this would be the same as `/home/<user>/.octoprint` under a default installation.

### mjpeg-streamer

The server is running when the container starts, but in your octoprint config, you might need to configure the stream URL to point to the IP address of the machine running.

## USB Devices

If you dont want to run the container under privileged, you will need to add each device (tty*) to the `docker-compose.yml`
