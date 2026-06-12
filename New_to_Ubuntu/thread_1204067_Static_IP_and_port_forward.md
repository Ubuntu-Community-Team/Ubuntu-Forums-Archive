---
title: "Static IP and port forward????"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by andjen on 2009-07-04
I have a dual boot system with Hardy Heron and Vista.

I need to set up a static IP and port forward in Ubuntu so that I can use bittorrent.

Whilst using Vista it was not really a problem because portforward.com walked me through all the steps that I needed to take with the router that I've got. But that site doesn't cater for Linux/Ubuntu and so I'm in need of some help because I really **don't** understand all this networking stuff DCHP, DNS etc.

'Ifconfig' (heard about somewhere!) shows :

eth0      Link encap:Ethernet  HWaddr 00:19:66:58:b4:05  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe58:b405/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:850461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:801449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:729828829 (696.0 MB)  TX bytes:156942505 (149.6 MB)
          Interrupt:253 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:350500 (342.2 KB)  TX bytes:350500 (342.2 KB)

My router is a Netgear DG834G and to access the router setup I put 
192.168.0.1 into my browser.


Can anybody help (or do you need more info).

---

### Post by kpkeerthi on 2009-07-04
The easiest way is to leave Ubuntu use DHCP and configure your router to serve your PC a fixed IP. Check in your router's control panel.

---

### Post by cb951303 on 2009-07-04
Port forwarding is done via router. If you did it once then it stays there even though you wipe Vista and install Ubuntu. You just have to give Ubuntu, the same static IP number that you had in Vista.
You can set a static IP via network manager.

---

### Post by Iowan on 2009-07-04
It's a tradeoff whether it's easier to set up a static lease on your router, or configure a static address in Ubuntu.  Neither method should require to modify the port-forwarding configuration in your router. (Personally, I'm fond of setting up the DHCP server - router in your case - to issue a static lease... but it's your choice.)

---

### Post by diablo75 on 2009-07-05
> **kpkeerthi said:**
> The easiest way is to leave Ubuntu use DHCP and configure your router to serve your PC a fixed IP. Check in your router's control panel.

Not all routers are capable of this (namely, Linksys routers).

---

