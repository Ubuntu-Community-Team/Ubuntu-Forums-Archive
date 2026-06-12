---
title: "[ubuntu] Router denies my connection with correct PASS Archer T4U V3"
date: 2020-04-17
forum: Networking &amp; Wireless
---

### Post by mcslk27 on 2020-04-17
Hello everyone, few day ago I bought an TP-Link Archer T4U V3 for use by Ubuntu 18.04 Platform.


I had a few problems with a drivers but I got it right fortunetly after few hours of battle. My card is now visible in the system. My problem is that I can not connect to my Wireless home net (both 2.4 and 5 GHz), more over it's not even possible to connect to my smartphone hotspot.


It looks like net denies password and requests for another one after few seconds. I'd be grateful for any tips.


Thanks!

---

### Post by CelticWarrior on 2020-04-17
So, this has nothing to do with the router because > it's not even possible to connect to my smartphone hotspot. The problem is with the WiFi dongle itself and/or the drivers you installed.

Let's start by identifying your hardware and what sort of drivers were installed.
Please run 'lsusb' and post here the relevant line about the WiFi dongle along with a description of what drivers you installed, where did you get those from, and what you did to install them.

---

### Post by mcslk27 on 2020-04-17
Okey so lsusb response this:

*marcin@platform:~$ lsusb*
Bus 001 Device 003: ID 2357:0115 

This is ID of my WIFI dongle. Card started to be recognized after steps described by chilli555:
[https://askubuntu.com/questions/1182192/ubuntu-not-recognizing-archer-t4u-us-3-0-properly](https://askubuntu.com/questions/1182192/ubuntu-not-recognizing-archer-t4u-us-3-0-properly)

I also blacklisted another drivers I tried to install: rtl8812au, rtl8821ae, rtl8822be and 8822bu.

---

### Post by Autodave on 2020-04-17
Someone much higher in pay grade will likely have to be the one who helps you, but let me suggest one thing that may help: I actually have a machine like this and so does a friend of mine.

I cannot type my password in: it will fail repeatedly.  BUT, if I type the password into a document and then copy and paste it into the box when requested, it works!  Why?  Not a clue.  But it does.  And it will only take about a minute of your time to try.

---

### Post by mcslk27 on 2020-04-18
Not this time my Friend, but thank you for a tip!

---

