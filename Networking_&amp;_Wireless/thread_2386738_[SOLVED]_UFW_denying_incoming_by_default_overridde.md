---
title: "[SOLVED] UFW denying incoming by default overridden"
date: 2018-03-09
forum: Networking &amp; Wireless
---

### Post by fishb6nes on 2018-03-09
Edit: Turns out that running a docker container with the -p tag messes  with iptables directly which doesn't reflect in ufw status 
[https://askubuntu.com/questions/652556/uncomplicated-firewall-ufw-is-not-blocking-anything-when-using-docker](https://askubuntu.com/questions/652556/uncomplicated-firewall-ufw-is-not-blocking-anything-when-using-docker)
Running the container with -p 127.0.0.1:6379:6379 as suggested seems to work perfectly. Thanks all.

Hello, while attempting to secure a Redis Docker instance with UFW I noticed that incoming trafic isn't denied by default at all. Even when denying a port explicitely (6379 in this case) I could still remotely connect to the Redis server and retrieve data.

The server is running Debian 9.3 with the latest OVH kernel (I hope that isn't relevant)

 I ran the docker instance as per [https://docs.docker.com/samples/library/redis/](https://docs.docker.com/samples/library/redis/)
```
docker run --name some-redis -p 6379:6379 -d redis
```

I stumbled upon [https://ubuntuforums.org/showthread.php?t=2350980](https://ubuntuforums.org/showthread.php?t=2350980) who had a similar issue (but different in the end) who was requested some extra information and logs which I will add below.

Thank you so much for taking a look,

Edit: Logs removed, see edit above.

---

### Post by mörgæs on 2018-03-10
Thanks for marking the thread solved but better to use Thread Tools.

---

