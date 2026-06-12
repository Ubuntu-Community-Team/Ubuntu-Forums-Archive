---
title: "ndiswrapper woes..."
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by Barrucadu on 2007-05-11
I have managed to install all my wireless drivers for my dongle through ndiswrapper, but when I run "modprobe ndiswrapper", it just terminates with "FATAL: Module ndiswrapper not found."
I've installed the ndiswrapper-common and the ndiswrapper-utils .deb files (would use apt-get, but no way for me to get internet on that laptop yet)

---

### Post by jglen490 on 2007-05-11
Did you run > ndiswrapper -m before the m odprobe?

---

### Post by Barrucadu on 2007-05-12
```
barrucadu@barrpc:~$ sudo su
Passsword:
root@barrpc:/home/barrucadu# ndiswrapper -m
module configuration already contains an alias directive

root@barrpc:/home/barrucadu# modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
root@barrpc:/home/barrucadu# 
```

---

### Post by Barrucadu on 2007-05-12
I just found a tutorial to set up ndiswrapper & netgear drivers that requires compiling ndiswrapper myself, so i'll try that.

Well, I have somehow broken ubuntu. It won't boot. Time for a fresh install! lol

---

### Post by Barrucadu on 2007-05-12
I have followed the instructions here: [https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

BUT - when I run "sudo iwconfig wlan0 essid WHN mode managed", it returns:
```

Error for wireless request "Set ESSID" (8B1A) :
     SET failed on device wlan0 ; No such device.
```

---

### Post by Barrucadu on 2007-05-12
I have rebooted, and now ubuntu freezes whenever I plug the dongle in, help!

---

