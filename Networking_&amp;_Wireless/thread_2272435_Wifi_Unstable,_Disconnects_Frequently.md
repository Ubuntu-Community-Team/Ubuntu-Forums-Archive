---
title: "Wifi Unstable, Disconnects Frequently"
date: 2015-04-06
forum: Networking &amp; Wireless
---

### Post by Billy_Branch on 2015-04-06
First off I'm sorry if this has already been posted, I've looked through several similar threads and tried some "solutions" that didn't work for me.


I'm using Ubuntu 14.10 on a desktop computer I build a few days ago, and since I first started Ubuntu the wireless connection has been temperamental. I am using a usb wifi adapter. I can connect to WiFi without a problem, but eventually I'm not able to load anything, though Ubuntu says I am still connected. This can be temporarily fixed by disconnecting and then reconnecting, but in a few minutes the problem arises again and I have to disconnect and reconnect.


I uninstalled network manager and am using Wicd. It didn't fix my problem but I like Wicd, however I could switch back to network manager if need be. 


I'm new to Ubuntu, having started using it 2 days ago, so please explain any necessary terminal commands and such to me so I can understand and learn. :D

I attached the wireless script from the sticky thread.

When I do lsusb I get this:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 258a:0001  
Bus 004 Device 002: ID 5543:0781 UC-Logic Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 093a:2521 Pixart Imaging, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 017: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Thanks for any help!

---

### Post by jeremy31 on 2015-04-06
Have you tried this fix [http://ubuntuforums.org/showthread.php?t=2251402&p=13159739#post13159739](http://ubuntuforums.org/showthread.php?t=2251402&p=13159739#post13159739)

---

### Post by Billy_Branch on 2015-04-06
You know what, I think that may have done it! Thank you, I'm glad it was that easy. I had viewed that forum you linked me to earlier but didn't try the fix.

I tested the internet for a few minutes and it stayed working, so I'll mark the thread as solved. Thanks again!

---

