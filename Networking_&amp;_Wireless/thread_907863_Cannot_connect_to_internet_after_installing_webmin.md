---
title: "Cannot connect to internet after installing webmin"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by nemesis_vii on 2008-09-01
Hi, I have just installed webmin 1.430 on my pc.
My OS  is ubuntu 8.04 desktop.

after installing and configuring the webmin firewall ( from a tutorial on the web )
It appears that  my ADSL connection is not working ... I believe the problem is been caused by the wrong  fire wall setting .. but I don't know how to solve the problem ..
recently I found that whenever I want to connect to the internet I have to log into webmin and goto network menu and click on firewall and then click on apply setting ( there is no setting , I deleted all the old setting and set the fire wall to accept all incoming and out going traffic) and then my pc is connected.
but I have to do this every time I reboot.

Please someone help me...
it's really boring to do that process every time.

My ADSL modem is connected to my PC on eth0
HWaddr has been removed by me :)

below is my ifconfig result:

eth0      Link encap:Ethernet  HWaddr --:--:--:--:--:--  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:61ff:fe46:cbf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33310339 (31.7 MB)  TX bytes:3242921 (3.0 MB)
          Interrupt:19 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr --:--:--:--:--:--  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:398951 (389.6 KB)  TX bytes:398951 (389.6 KB)



wlan0     Link encap:Ethernet  HWaddr --:--:--:--:--:--  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19

---

