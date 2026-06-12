---
title: "Ubuntu 17.04 unable to connect to any WiFi"
date: 2017-10-14
forum: Networking &amp; Wireless
---

### Post by marcosarac on 2017-10-14
Hi everyone, I'm new to this forum and to the Ubuntu world. I've got a problem with my freshly installed Ubuntu 17.04, I can't connect to any WiFi network cause it seems out of range even though I can connect in Windows. I've tried different solution found in various forums but they don't work for me. Can anybody help me?

---

### Post by jeremy31 on 2017-10-14
See the wireless script link in my signature and post results

---

### Post by marcosarac on 2017-10-14
I'm currently unable to connect to any Ethernet cable because I would have to move my entire PC. Is it possible to solve without an internet connection?

---

### Post by jeremy31 on 2017-10-14
See [https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385) under Method 2

---

### Post by marcosarac on 2017-10-16
Here is my result 
[http://paste.ubuntu.com/25752845/](http://paste.ubuntu.com/25752845/)

---

### Post by praseodym on 2017-10-16
[https://ubuntuforums.org/showthread.php?t=2374421&p=13698647#post13698647](https://ubuntuforums.org/showthread.php?t=2374421&p=13698647#post13698647)

Change the driver

---

### Post by jeremy31 on 2017-10-16
```
sudo ifconfig wlp3s0 up
```
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot

---

