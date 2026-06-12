---
title: "No Ethernet connection after Ubuntu 14.04 LTS install"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by loren41 on 2014-10-28
Removed Windows XP from my Dell Inspiron 1520.  Burned a Ubuntu 14.04 LTS DVD and installed successfully on the laptop.  Prior to the install, the pc showed an active Ethernet connection to my working router.  The connection dropped and the updates were not made.  Install crashed, asking for log files.  With no connection, this could not be done.

Tried swapping cables and rebooting with no luck.  iconfig shows only lo.  Network manager contains no info.  Should I supply something?  Need assistance.

Before the 14.04 install, I tried ver. 8.10 and etho was there!

---

### Post by Hadaka on 2014-10-28
Hi, let's get some data and see what is happening.
please COPY and paste then post the output of..
```
lspci -n | egrep '0200|0280' | awk '{print $3}'
rfkill list all | grep yes
lsmod | egrep 'wl|b43|tg3'
```
thanks

---

### Post by loren41 on 2014-10-28
Hi Hadaka.  The following is the output desired.

loren41@loren41-Inspiron-1520:~$ lspci -n | egrep '0200|0280' | awk '{print $3}'14e4:170c
14e4:4311
loren41@loren41-Inspiron-1520:~$ rfkill list all | grep yes
loren41@loren41-Inspiron-1520:~$ lsmod | egrep 'wl|b43|tg3'
wl                   3999690  1 
lib80211               14040  1 wl
cfg80211              409394  1 wl
loren41@loren41-Inspiron-1520:~$

---

### Post by Hadaka on 2014-10-28
Hi please connect your wired ethernet connection and then
copy and paste the following.,
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #Ignore any errors or cant find
```
boot
,,,your wired should now be woking
while connected to the internet please do..
```
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
disconnect the wired ethernet.boot
test wireless

---

### Post by loren41 on 2014-10-28
Hadaka,
We did it!  Your process solved the mystery.  Now I must look back at what you sent me and my machine responses to learn what was done.  Thanks, and now on to making a wireless connection.

Do you mark the thread solved, or do I have to do something?
Loren41

---

### Post by Hadaka on 2014-10-28
Glad that worked for you.
to mark the thread solved,
how to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

