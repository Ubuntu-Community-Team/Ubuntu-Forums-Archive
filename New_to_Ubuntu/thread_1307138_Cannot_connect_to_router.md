---
title: "Cannot connect to router"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Draist on 2009-10-30
I just bought a router and cannot connect to it while I'm in ubuntu. I had Ubuntu configured for My ADSL modem just fine.  I havnt been able to ping it in Ubuntu at all.  It works fine in Windows but I'm clueless when it comes to setting this up.  Any help will be greatly appreciated.

---

### Post by k3lt01 on 2009-10-31
Your router is probably not the issue at all. Try [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") and see if it works.

---

### Post by Draist on 2009-10-31
Still not able to ping or connect to the router.  When I ping it it says network is unreachable.  I've never set up a network with ubuntu before so I'm probably just missing some simple first step like releasing the previous setting or something.


Edit:  Its defiantly something to do with my previous setting cause if I live boot then it connects immediately.  So all I have to do is reset my old connection somehow.

---

### Post by Iowan on 2009-10-31
Does machine get IP address (**ifconfig -a**)?

---

### Post by viper250 on 2009-10-31
If your router is a wireless router and you are trying to connect wireless to it you may be getting a conflict, most adsl modems have a wireless connection and connecting a wireless router to it may cause a problem. make sure your patch cable between the adsl and router are plugged into the correct port on the router your documentation for your router should have the info. If the hardware is not the problem then the network setting is probably at fault.

---

### Post by Draist on 2009-10-31
Its defiantly something to do with My previous PPPOE connection.  I installed it using pppoeconf but don't know how to get rid of the settings.

Its a wireless router but I have it connected via cable to the desktop.  All the cables are in the right place and I've set up the router using Windows and it works fine for both wired and wireless devices in my house.  Just not when I boot Ubuntu.


ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1c:25:6c:15:db  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)


pan0      Link encap:Ethernet  HWaddr 9e:b7:f0:0b:a5:26  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

