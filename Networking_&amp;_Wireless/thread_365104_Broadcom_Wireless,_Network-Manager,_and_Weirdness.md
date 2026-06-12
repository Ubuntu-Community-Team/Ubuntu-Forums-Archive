---
title: "Broadcom Wireless, Network-Manager, and Weirdness"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by qiemem on 2007-02-19
Got a broadcom 4306 wireless card which I got (mostly) working via this tutorial: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174). 

My wireless works at first, but after a while, the network connection icon still says its got signal and everything, but nothing can seem to connect until I restart the computer. It is usually receiving packets, but only sends a few if any. iwlist scanning returns a list as it should. Oh, one more thing. The network connections thing shows full connectivity pretty much at all times, even when I've moved far out of the range of the network. The dropdown menu in properties is blank (I have to type in the essid my self). 
Furthermore, network-manager used to work fine. But now it shows nothing but a grayed out wired connection box.

Anyway, this is very frustrating and would appreciate any input on this issue. It is especially problematic moving from network to network, which I do on a regular basis. Thanks in advance for any help!

---

### Post by Comedy Dave on 2007-02-19
> **qiemem said:**
> Got a broadcom 4306 wireless card which I got (mostly) working via this tutorial: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174). 

My wireless works at first, but after a while, the network connection icon still says its got signal and everything, but nothing can seem to connect until I restart the computer. It is usually receiving packets, but only sends a few if any. iwlist scanning returns a list as it should. Oh, one more thing. The network connections thing shows full connectivity pretty much at all times, even when I've moved far out of the range of the network. The dropdown menu in properties is blank (I have to type in the essid my self). 
Furthermore, network-manager used to work fine. But now it shows nothing but a grayed out wired connection box.

Anyway, this is very frustrating and would appreciate any input on this issue. It is especially problematic moving from network to network, which I do on a regular basis. Thanks in advance for any help!


I am having a similar problem with my Linksys wusb54g v4 wireless adapter.
Please Help!

---

### Post by qiemem on 2007-02-20
Update:
I've uninstalled network-manager and am trying wifi radar instead. I have had considerably greater luck with wifi radar, though I still usually have restart my computer when moving from one network to another. Note: I had to manually remove the network-manager from starting up via the sessions dialogue. Also, wifi radar takes a little tinkering to get working, but not a whole. Anyway, that might help others with a similar problem.

---

