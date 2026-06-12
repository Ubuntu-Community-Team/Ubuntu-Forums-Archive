---
title: "forward jupyter server over ssh"
date: 2024-04-23
forum: Networking &amp; Wireless
---

### Post by jakubmitura14 on 2024-04-23
Hello I want to connect from my ubuntu laptop to my ubuntu pc. I managed to establish ssh and it works (I enabled and mapped port 8888 via router) When I run docker container like below
```
docker run -p 8888:8888 -p 49053:49053 -v /media/uzytkownik/hddData/datasets/slicer_data:/home/sliceruser/work --rm -ti lassoan/slicer-notebook:latest
```
It give the link to jupyter server (from inside docker that i run on host machine - PC).
```
[http://127.0.0.1:8888/?token=8e3d33eef29d156543636499124673c82eceb2787f333dff](http://127.0.0.1:8888/?token=8e3d33eef29d156543636499124673c82eceb2787f333dff)
```
When I try to open this link on my PC all work, but from laptop connected via ssh via browser it give error
```
This site can’t be reached 127.0.0.1 refused to connect
```
I suppose it is related to the fact that browser is not connected via ssh , still I would be thankfull for anybody guiding me how to resolve the issue.

Thanks

---

### Post by Holger_Gehrke on 2024-04-23
The address '127.0.0.1' is one of the addresses assigned to the loopback interface. It's meant exclusively for accessing servers running on the same machine as the client. So your browser on your laptop is trying to connect to whatever waits on port 8888 on your laptop (nothing there, so connection refused). If your laptop and the server are on the same network, you can try to find out the address of the server ('ip addr' on the command line of the server) and try that address in the browser. If you're trying to connect from the laptop outside of your LAN it gets more complicated. Look in the manual for ssh and search for 'TCP FORWARDING'.

Holger

---

### Post by jakubmitura14 on 2024-04-24
ok thank you I will try that !

---

