Docker Infrastructure Tools
===========================

Infrastructure tools related to using Docker.

dockstart
---------

Wrapper script for `docker start`.

Manages the lifecycle of a docker container on behalf of a process
control mechanism such as supervisord. This is necessary because
the docker client does not pass signals via the daemon to the
running container, when those signals are not sent from the
terminal. This script is necessary as of Docker version 0.8.0.
See:

 * https://groups.google.com/d/topic/docker-user/bC0mabJXmJ0/discussion
 * https://github.com/dotcloud/docker/issues/1311

This script should be started as follows:

    dockstart <container>

A TERM, INT, or QUIT signal received by the wrapper will be translated to a
"docker stop" command rather than being forwarded directly to the docker
client process.

A HUP signal received by the wrapper will be translated to a
"docker restart" command.

If the wrapper script is force killed, the underlying container will
continue to run.
