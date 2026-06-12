---
title: "Broadcom / HP Wireless Woes"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by itzpapalotl on 2007-01-10
So CLose...
Soooooooo close.
Okay. So I installed dapper on my hp nx9600 laptop. In all fairness I have been arned about linux and laptops, but absolutly everything just plain worked right out of the box. My screen resolution is fine at 1400 x 900 the LAN card fires up, I can get online if there's a port, I have everthing working. except.. and I expect you've all heard this before... except the wireless card. 

it one of these:
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

No I've been through maybe a thousand pages of instructions, and I know a fe things that are going on:
Like for instance:
It's there
Ubuntu recognises it.
There is a driver installed
It even acts like it should connect.

What I think is the problem is that the little button that is used to turn wireless on and off in windows  is set to default off and the button itself is not recognised by ubuntu. So my wireless is there, its installed, its working, but it's off.
and I cant turn it on.
I have been led to believe that some of you out there have been successfull with this distro on this machine with this broadcom card.. Any help would be GREATLY appreciated.
I can DL things with windows and use my USB stick to get them over to Dapper if need be. (Oh yeah... no cable connection at my place. Wireless only.

---

### Post by teaker1s on 2007-01-10
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by ElvisThePelvis on 2007-06-08
This works without ndiswrapper:

[http://ubuntuforums.org/showpost.php?p=1189151&postcount=332]("http://ubuntuforums.org/showpost.php?p=1189151&postcount=332")

---

### Post by khha4113 on 2007-06-08
I have exact same model like your wireless Broadcom board, and I just followed the guide from this [http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946) to install.
It works great.

---

