---
title: "No wlan on iwconfig or ifconfig. ifcongig wlan up does not work."
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by samus man on 2008-07-05
EDIT: Issue solved.

I'm having some trouble setting up the wireless card on my Dell Inspiron 1420.  (I know I can get Ubuntu pre-installed on my machine, but I received it as a gift and the giver chose the Windows version.)  I've been trying to get the wireless up and running, but I've been running into some issues.

This is my console output for ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1c:23:fe:66:28  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fefe:6628/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49786674 (47.4 MB)  TX bytes:7682126 (7.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84000 (82.0 KB)  TX bytes:84000 (82.0 KB)


Output from ifconfig wlan up
wlan: ERROR while getting interface flags: No such device


As an additional note, when I reboot from Windows to Linux, my wireless light remains on from windows, but ifconfig still doesn't turn up anything interesting.  When I cold boot Linux, the wireless light does not turn on.  The wireless card switch does nothing.

Additionally, lpsci reports the following...
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


Additionally, I have ndiswrapper set up with the proper drivers, but according to the ndiswrapper gui, I don't have wireless hardware.

Any way I can get wlan to...show?  I'm pretty sure it's the last thing stopping me from having a wireless Linux.

---

### Post by kevdog on 2008-07-05
Please post lshw -C network and browse this thread:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by samus man on 2008-07-05
Alright, I've read through the information on the thread you linked to.  However, I am running into problems with lshw -C network.  This is the output:

```
PCI (sysfs) 
```

Apparently, lshw never finished running.  I had to ctrl+c it.



EDIT: Problem solved.  Thanks for your help.  Ended up adding an entry for wlan myself and now my wireless works great.

---

