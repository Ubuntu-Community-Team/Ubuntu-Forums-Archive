---
title: "Forward IP address for NVR"
date: 2017-01-21
forum: Networking &amp; Wireless
---

### Post by serverman2020 on 2017-01-21
Hi Guys,

Linux semi-newbie here. I currently have two home linux systems running at the moment - one ubuntu server and one NVR.

At the moment, my home network is running on the IP address of 192.168.0.XXX with the IP of the NVR being 192.168.0.195

The NVR has a seperate subnet(?) for the IP cameras of 10.1.1.XXX

My goal is to try to access the 10.1.1.XXX cameras from the main network. After doing some homework, it seems I need to forward the ports of these IP cams. Unfortunately, the NVR doesnt allow this through the User Interface. The NVR has a linux busybox system running on it - luckily I managed to connect to the Busybox system via telnet CLI. 

SOOOO I think I'm halfway there... somehow I need to edit some files in the telnet connection to foward say cam one 10.1.1.1 to 192.168.0.195:1

Eventually my plan is to have the NVR and the ubuntu server both recording (ubuntu sever via zoneminder etc). I don't have a POE switch, so thats why I'd like to keep my cameras connected to the NVR. 

Does anyone know how I can acheive this? Am I on the right path??

---

### Post by lisati on 2017-01-21
Dupe of [https://ubuntuforums.org/showthread.php?t=2350165](https://ubuntuforums.org/showthread.php?t=2350165) closed

---

