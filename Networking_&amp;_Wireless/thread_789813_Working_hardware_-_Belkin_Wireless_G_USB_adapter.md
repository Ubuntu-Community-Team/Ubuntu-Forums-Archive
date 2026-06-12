---
title: "Working hardware - Belkin Wireless G USB adapter"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by agamotto on 2008-05-10
Hallo all, I just wanted to pass long the good news that on multiple computers running 8.04, the Belkin Wireless G USB network adapter does 'just work!'  Specs: model f5d7050, ver. 4001.  These are widely available at Walmart and Target.

YAY!!!!:biggrin::biggrin::biggrin::

---

### Post by cdw38 on 2008-05-16
Yes, I have this adapter as well.  Nice to see it "just working," but...

I am having a strange slowdown whenever anything starts downloading or uploading for any period of time.  Are you having similar problems?  It's not USB-related as I use an external USB hard drive without any problems.  Strangely, it doesn't really happen when I am just transferring fiiles between computers in my LAN, but when I am using Bittorrent or using APT to download packages the computer is barely usable.  

I wasn't having any of these problems when using a hardwired connection.

I will give this adapter a try on a couple other PCs and report back, just wanted to see if you are having any problems.

Model No. F5D7050 FCC ID K7S-F5D7050B

Here's ifconfig output as well:
wlan0     Link encap:Ethernet  HWaddr 00:17:3f:13:b2:41  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe13:b241/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12742759 (12.1 MB)  TX bytes:5032120 (4.7 MB)

Thanks if anyone has any suggestions.

---

### Post by cdw38 on 2008-05-16
Definitely is the adapter...I have Version 3, maybe 4 works better?  Tried it on my 64-bit Hardy Ubuntu install first, then on a Xubuntu Hardy install on my laptop (32-bit) and got the same slowdown problems.

---

