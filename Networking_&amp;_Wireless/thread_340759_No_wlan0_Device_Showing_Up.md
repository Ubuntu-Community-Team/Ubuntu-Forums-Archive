---
title: "No wlan0 Device Showing Up"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by falcon1 on 2007-01-17
Hey everyone. I recently installed Ubuntu 6.10, and I am having some trouble getting wireless working. When I go to the network connections, I only see two devices: lo, and eth0. I followed the ndiswrapper installation guide, but it didn't work. 

I am running a Dell Inspiron 9100 (the card is a Dell Wireless WLAN 1350 WLAN Mini-PCI Card). Thanks for helping me out! It really appreciated :)

---

### Post by spd106 on 2007-01-17
We could do with a bit more information. Have you been through this page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)?

Can you outline where you got up to and which packages you have installed. Plus maybe the output from **ndiswrapper -l**.

---

### Post by falcon1 on 2007-01-17
Alrighty...lets see. I used this guide: [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

I went through the whole thing. Should I still go through the link you send me?

Here is the output from ndiswrapper -l:
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx

Thanks!

---

### Post by spd106 on 2007-01-18
Ok, now check that ndiswrapper has been loaded, **lsmod | grep ndis**. If you get nothing, it hasn't, so you need to load it through **sudo modprobe ndiswrapper**.

You can also check through **sudo lshw -C network**. This will give you device specific information, such as the driver used and interface name.

---

