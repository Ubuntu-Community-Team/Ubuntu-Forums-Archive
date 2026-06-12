---
title: "Error when installing Ralink rt73 Driver"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by Matt Heath on 2007-05-14
I was following the instructions at
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))
and when I entered the command "make" it tells me
```
make:*** /lib/modules/2.6.15-28-386/build: No such file or directory. Stop.
make: *** [all] Error 2
```
Can anyone tell me what I need to do to make the right file exist?
EDIT: Actually I didn't follow the instructions exactly because I needed to install the .deb files for missing packages from a flash memory stick. From then on the only thing different was the number of the driver though.

---

### Post by Austin_KW on 2007-05-14
try these instructions [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by Matt Heath on 2007-05-16
Thanks, Austin. That didn't work either, but I think I've found the problem. The kernel I have installed is for 386 when my computer is 686. So I've put all the 686 things on but it looks for the 386 ones.

---

### Post by dolphs on 2007-05-19
Hi, sorry being a n00b but which packages are you referring to please. I want to try to set up my WLAN in Ubuntu 7.04 server. Anything else as "build-essential" and "install linux-headers-*" please ?

---

