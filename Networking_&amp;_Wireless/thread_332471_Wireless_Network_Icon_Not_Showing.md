---
title: "Wireless Network Icon Not Showing"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by ubunton on 2007-01-06
Hi,
I'm having a problem setting up wireless connection on my ubuntu edgy desktop.
I am using a dell 1390 ExpressCard and have used the [bcm43xx method]("http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear") for installing drivers. It seems like it worked, because i get a wireless connection showing in the network-settings configuration tool, and the LED which indicates that the card is working is on. It also turns off if i disable the wireless connection in the network-settings tool.

My only problem is that no wireless connection shows in the network manager icon. Both the default one and network-manager-gnome. They only show a wired connection. I've tried to tick and untick the "wireless" checkbox in the network-settings tool, didn't do any good...

And to provide some extra details, typing iwconfig eth1 yields:
--------
eth1      Link encap:Ethernet  HWaddr 00:14:A5:96:22:73  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe96:2273/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:211770 (206.8 KiB)  TX bytes:16819 (16.4 KiB)
--------

I'm guessing this must be caused by something silly, but can't figure it out.
Help?

---

### Post by ubunton on 2007-01-06
anyone?:confused:

---

### Post by ubunton on 2007-01-06
OK i figured it out.

the bcm43xx-cutter method doesn't work very well for dell 1390 apparently. I ended up using [a different guide]("http://pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505") and the ndiswrapper method. Just had to compile the latest version of ndiswrapper.

---

