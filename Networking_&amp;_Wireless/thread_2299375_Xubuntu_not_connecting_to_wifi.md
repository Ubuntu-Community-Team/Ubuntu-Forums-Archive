---
title: "Xubuntu not connecting to wifi"
date: 2015-10-17
forum: Networking &amp; Wireless
---

### Post by alex067 on 2015-10-17
I recently got a new laptop, windows 10, and have installed the latest version of xbunutu. However, none of my wireless options are coming up on xubuntu.

When I click on the network tab, I get these options:
Ethernet network
Wired connection 1
Disconnect

VPN connections

enable networking

---

### Post by Bucky Ball on 2015-10-17
*Thread moved to **Networking & Wireless**.*

Welcome. We are going to need more information than that to help. Ubuntu release and the output of this from a terminal for a start:

```
sudo lshw -C network
```

... and a description of what works, what doesn't, what you've tried, and what is happening when you try to connect. 

Outline your issue and what's happening as specifically as possible. Good luck. :)

---

### Post by alex067 on 2015-10-17
When I put in that command, the following is outputted;

-network
description: Ethernet interface
product: 82540 EM gigabit ethernet controller
vendor: intel
phsycail id: 3
bus info: pci@0000:00:03.0
logical name: eth0
version: 02
serial: 09:00:27:30:4b:a1
size: 1Gbit/s
capacity: 1Gbit/s
width: 32 bits
clock: 66 mhz
capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotion
configuration: autonegotiation=on broadcast=yes driver =e1000 driverversion=7.3.21-k8-NAPI duplex=full latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed = 1Gbit/s

---

### Post by Hadaka on 2015-10-17
hi, with a working wired connection please do..
```
sudo apt-get update && sudo apt-get upgrade
 sudo apt-get autoremove && sudo apt-get autoclean
```
reboot,disconnect the wired connection test wireless

---

### Post by alex067 on 2015-10-18
Is this normal? when I did the update command, I get a lot of :

W: failed to fetch us.archive.ubuntu
W: failed to fetch us.archive.ubuntu
W: failed to fetch security.ubuntu.com

same for the upgrade command

---

### Post by alex067 on 2015-10-18
I have done what you said, rebooted my pc, turned on xubuntu but nothing has changed, my wifi name is: UNIVERSITY HOUSE but nothing comes up when I pull the network tab

---

### Post by Bucky Ball on 2015-10-18
You need to be online with a cable to do the updates/upgrades/autoremoves. Get online with a cable and:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

... one command at a time, hitting return after each so we can see specific errors if they occur, then:

[QUOTE=Hadaka]reboot,disconnect the wired connection test wireless [/QUOTE]

Please post terminal stuff between [code] tags (see last link in my signature).

---

### Post by Hadaka on 2015-10-18
Hi, if the ssid is UNIVERSITY HOUSE then..i would suggest an underscore to eliminate the space  UNIVERSITY_HOUSE
spaces arnt a good idea. also...if it is a university network...that is a whole different issue.
please go here,,read carefully..and post the wireless-info.txt file
if you run it correctly..that txt file will be in your home directory
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
thanks

---

### Post by alex067 on 2015-10-18
I do not understand what I have to do with this text file? And it will  not be in my home directory for ubuntu since I will be downloading it  through my normal OS and not through xubuntu

What should I do?? It seems the solution is connecting with an ethernet cable but there is no modem here to connect to

---

### Post by Hadaka on 2015-10-18
when you loaded lubuntu..did you load it with the updates???
this command..
```
sudo apt-get update && sudo apt-get upgrade
```
insures that you have the latest updates, not only are they for security issues
but also for kernel updates and driver updates.Its very difficult to determine what
is causing your issue when what you loaded is not yet complete and you have zero
access to the internet.please post the output of these commands.
```
lspci -nnk | grep -iA2 net
lsmod
rfkill list all
```and use code tags to report the results.
there are instructions on Buckyball's signature
thanks.,

---

