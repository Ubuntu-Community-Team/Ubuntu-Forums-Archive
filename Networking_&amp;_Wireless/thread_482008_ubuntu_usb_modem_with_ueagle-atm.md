---
title: "ubuntu usb modem with ueagle-atm"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by seladin on 2007-06-23
hello

2 months ago I installed ubuntu on my pc and connected a usb modem with ueagle-atm using following link: [http://ubuntuforums.org/showthread.php?t=144468&highlight=sagem+fast+800](http://ubuntuforums.org/showthread.php?t=144468&highlight=sagem+fast+800)

It was quite good but then yesterday it stopped working. ifconfig gives somethink like:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

and plog gives:
	  Jun 23 13:25:46 hezanic pppd[4759]: Plugin pppoatm.so loaded.	  
          Jun 23 13:25:46 hezanic pppd[4766]: pppd 2.4.4b1 started by polat, uid 1000
	  Jun 23 13:25:46 hezanic pppd[4766]: Using interface ppp0
	  Jun 23 13:25:46 hezanic pppd[4766]: Connect: ppp0 <--> 8.35
	  Jun 23 13:26:16 hezanic pppd[4766]: LCP: timeout sending Config-Requests
	  Jun 23 13:26:16 hezanic pppd[4766]: Connection terminated.
	  Jun 23 13:26:16 hezanic pppd[4766]: Modem hangup

any help appriciated. I thought to uninstall ueagle and reinstall it but i don't know how to uninstall ueagle-atm.

---

