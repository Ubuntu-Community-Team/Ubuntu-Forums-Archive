---
title: "[SOLVED] Please Help"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Fistols on 2008-02-11
Hi, I am having trouble with my wireless connection. First off it says I dont have one in my connections manager. And when I type lshw -C network i get :

 *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e2:47:e8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=137.142.88.140 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


and thats it. Where is my Wireless connection?!?!
TO try to get it working I downloaded the windows 98 drivers using the "WIndows Wireless Drivers" app from the Add/remove  applications tool. I finally got that working and i installed the RealTek 8187B drivers and it says my hardware is detected. SO why doesnt it work? Please let me know.
-Derek

---

### Post by kaginken on 2008-02-11
Derek,

Has this ever worked before?  Does it work on your windows system (if you're dual booting)?  I'm not familiar with a RealTek - is it in the supported hardware list?  Try googling that card with the cards model number and your laptop model, bet you'll either find a lot of help, or a lot of people complaining about how hard it is to set up...

Also, is your wireless indicator light on?  Most computers have a little wifi light that will light up (on internal wireless nics), or if it's an external wifi card, does that light up?  That's a good start also...

Not sure what else to tell you - good luck!  and rock on!  :guitar:

---

### Post by digitalhillbilly on 2008-02-11
If your card is really a realtek 8187b the winows drivers won't work for you - at least they didn't for me. I did try them and my card was detected and I could even scan all the networks in my neighbourhood but couldn't actually connect. There is a modified driver for that device that works perfectly for me.... I actually just got it fully functional a couple hours ago and ended the thread I was using to vent with a list of what I did. I don't think I left anything out.

Check the last post in this thread to see what I did: [http://ubuntuforums.org/showthread.php?t=689686](http://ubuntuforums.org/showthread.php?t=689686)

BUT first I recommend reading this thread. It has very valuable information about your wifi card, how to manipulate and modify it, a great list of commands, on an on: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

dh


btw... if you use the rtl8187b-modified driver you'll have to remove ndiswrapper

---

### Post by Fistols on 2008-02-11
Bh, first off, THANK YOU SO MUCH MAN!
That worked and I am very excited.
I will keep you updated if anything comes up with it.
Thanks again to everyone!
-Derek

---

