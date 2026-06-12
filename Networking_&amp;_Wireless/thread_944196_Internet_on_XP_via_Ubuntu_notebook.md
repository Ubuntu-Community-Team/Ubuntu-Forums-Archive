---
title: "Internet on XP via Ubuntu notebook"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by kramulous on 2008-10-11
Hi,

  I've had a ubuntu server which I just had to dual boot with XP.  Now I need Internet on the XP machine but cannot connect the box to the switch.

  I have another Ubuntu notebook with wireless that I'd like to connect the xp machine to via ethernet and share the notebooks wireless Internet.

  Can somebody help me with this.  An "ifconfig" on the notebook is:
> 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60124 (58.7 KB)  TX bytes:60124 (58.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:4d:2a:25  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe4d:2a25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1139806 (1.0 MB)  TX bytes:201807 (197.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-4D-2A-25-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2008-10-11
you would have to setup internet connection sharing(ICS) in ubuntu..[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by Iowan on 2008-10-11
[Here's]("https://help.ubuntu.com/community/Internet/ConnectionSharing") another one.

---

