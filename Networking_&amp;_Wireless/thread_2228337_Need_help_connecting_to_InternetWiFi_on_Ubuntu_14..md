---
title: "Need help connecting to Internet/WiFi on Ubuntu 14.04 [Dell Latitude 131L]"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by Justin.Daniels on 2014-06-06
First of all, I am brand new to linux. This is my very first attempt at installing and using a linux operating system.


  So, I downloaded Ubuntu 14.04 today, and I went about installing it  on my personal laptop. During the installation it asks you if you would  like to apply updates while the installation is being processed;  however, my laptop was already having issues connecting at the time, so I  could not select that option. I do not know if that has any effect on  the issue I am currently experiencing, but I thought I would mention  that.


  Ubuntu just finished installing, and it automatically has no  connections. I plugged in an ethernet cord to the laptop, and I still  couldn't get any sort of connections. 


  Any help would be greatly appreciated, as I have no idea where to even begin to fix my issue.


  Thanks,
Justin.Daniels

---

### Post by Hadaka on 2014-06-06
hi, please open a terminal  ctrl/alt/t  then COPY
and paste the following...
```
lspci -n | egrep '0200|0280' | awk '{print$3}'
```
post the output
thanks

---

### Post by Justin.Daniels on 2014-06-07
```
14e4:4311
14e4:170c
```

This is the output I receive.

---

### Post by Hadaka on 2014-06-07
Thanks, connect your ethernet cable so you will
have internet access when your card is activated.
please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #dont be concerned if this  command fails
sudo modprobe b44
```
boot.....you should now have wired internet
then do. with the cable still attached and connected to the internet
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot
you should now have wireless

---

### Post by Justin.Daniels on 2014-06-08
Worked perfectly, thank you!

---

### Post by Hadaka on 2014-06-08
Glad that worked for you .
please mark this thread solved
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

