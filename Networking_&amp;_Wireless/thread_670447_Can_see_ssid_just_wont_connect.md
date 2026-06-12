---
title: "Can see ssid just wont connect"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by m1k3uk on 2008-01-17
Hi first of all im new to linux so any help would be great.  I installed the latest version of ubuntu today with dualboot windows xp.  However i just cant get it connecting to the internet.  Im using a buffalo WLI-U2-KG54 usb adapter which works fine under xp but in ubuntu when i click on the network manager i can see a list of ssids and when i try to connect to mine it asks for the key but after ive input the key it thinks for a little while then the icon goes back to disconnected.

Im pretty sure by the fact i can see a list of ssids that the wireless adapter is installed??? maybe?  But it just wont connect.  Any ideas?

btw i just tried the command sudo iwconfig and it brought up my adapter as wlan0 but under the headings essid and key where just empty "" 

Any help is greatly appreciated!

---

### Post by Hightide on 2008-01-17
First of all have a go at Kevdogs tutorial. It may help.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

:)

---

### Post by m1k3uk on 2008-01-18
Ok il give that tutorial a try now and report back.  Just to let you no i had a hunch that the wifi manager didnt like my router so i tryed another 1 called wicd but that didnt work either :( il give that tutorial a go then.

Thanks

---

### Post by m1k3uk on 2008-01-18
Right ive just followed that tutorial and hit a problem at the 1st step i think.

After the command lshw -C network it should show my wireless device and drivers however mine only shows this:

description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:0d:0b:9f:e6:a0
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

As you can see it doesnt mention anything about the driver so ive tryed to update my driver using the 1's that work in windows using ndiswrapper.  I got the .inf and .sys files from windows and installed and everything was fine until i used this command:

sudo modprobe ndiswrapper

that gave me 

FATAL: module ndiswrapper not found

but when i installed it it said the driver was found just that command didnt work.  Any ideas anyone???

---

