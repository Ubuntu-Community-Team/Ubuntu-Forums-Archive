---
title: "Help!"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by TerribleTickler on 2007-07-15
I have installed Ubuntu 7.04 on my acer Aspire 5610Z and I can't even get a wired or wireless LAN
connection. What can I do I am freaking out. Please someone help me. I am very frustrtaed and 
my wife thinks I have lost my mind. I now have a great hatred against microsoft since they seem
to monopolize the hardware industry. My wireless network card dosen't work, my ehternet or
wired LAN card is giving me the finger and laughing at me, I don't even know if my chipset is 
needing an upgrade. I totally formated Vista off my hard drive in hopes of running a pure Linux
OS. Started out with Fedora 5 and now using or half way using Ubuntu 7.04 at this moment.
Most of my hardware just is not compatible.

---

### Post by ukripper on 2007-07-16
Can you post output of following commands  here  :

in terminal type:-

```
sudo lspci
```

```
sudo ifconfig
```

```
dmesg | grep tail
```

```
sudo gedit /etc/interface/networks
```

---

### Post by ukripper on 2007-07-16
hope this thread [http://ubuntuforums.org/showthread.php?p=3000502](http://ubuntuforums.org/showthread.php?p=3000502) would help to setup wireless for you and rest we will find out once you post output of above commands

---

