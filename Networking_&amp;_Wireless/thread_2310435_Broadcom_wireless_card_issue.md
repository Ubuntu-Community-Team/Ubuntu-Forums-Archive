---
title: "Broadcom wireless card issue"
date: 2016-01-19
forum: Networking &amp; Wireless
---

### Post by Ahmed_Zia on 2016-01-19
I have Broadcom BCM43142 802.11b/g/n Wireless Network Adapter in my laptop. 
When i run live version of Ubuntu from USB flash and go to settings and install additional drivers it install the WIFI drivers automatically for my network card.

But

When I install full version of Ubuntu on my laptop and go to settings for additional drivers it was not installing. 
I am feeling so bad about it.
Kindly help me to solve this Plz.

---

### Post by Bucky Ball on 2016-01-19
Welcome. Please use default font and point size. The rest is unecessary. Giant bold letters is considered shouting. You will discourage people from helping rather than encourage them. 

Please have a read of the sticky at the top of the Networking & Wireless area page 'Before posting in Networking & Wireless'.

Have you plugged in an ethernet cable, updated, and check Additional Drivers again? If not, do so, then reboot. If you click on the networking icon, do you see any available networks?

---

### Post by Ahmed_Zia on 2016-01-20
Yes i plugged in LAN cable too.
but its not working.
and also no no wifi networks when click on network icon

---

### Post by Hadaka on 2016-01-20
Hi, please open a terminal ctrl,alt,t and enter..
```
lspci -n | awk '/200|280/{print$3}'
```
post the output.
thanks.

---

### Post by Ahmed_Zia on 2016-01-27
14e4:4365
10ec:8136
ahmed@ahmed-HP-Pavilion-15-Notebook-PC:~$

Sorry for late  reply.

---

### Post by Hadaka on 2016-01-27
Hi, please follow this guide for your Broadcom [14e4:4365] card.
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
thanks

---

### Post by Ahmed_Zia on 2016-01-27
it shows something like this

14e4:4365 ------------------- -Special case #2 ---------------------bcmwl-kernel-source

---

### Post by Hadaka on 2016-01-27
Hi, from a working wired connection open a terminal - ctrl/alt/.t -
then copy and paste one line at a time.
```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
boot,remove wired connection and test wireless.
also please post the output of..
```
cat /etc/lsb-release
```
thanks.

---

