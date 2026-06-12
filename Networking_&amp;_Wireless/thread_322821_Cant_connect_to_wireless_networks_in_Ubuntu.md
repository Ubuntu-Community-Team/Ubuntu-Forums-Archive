---
title: "Cant connect to wireless networks in Ubuntu"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by arnold0 on 2006-12-21
Hello, in Network Manager I'm able to see all the networks so I figure the wireless card must be configured properly. The problem is that when I try to connect it says "connecting" for a few minutes then stops without connecting. The problem started when I was trying to connect to a WEP network but I have found since that I can't connect to any wireless networks at all. Wireless was fine in Ubuntu less than a day before the issue appeared, it all started after the WEP network problems, no idea whats causing it though.

Wireless works fine in Windows, even connected to the WEP network. Would be nice not to have to boot into Windows just for internet though.

Please reply if more information is needed and sorry for the ambiguity. Thanks

---

### Post by nsleiman on 2006-12-21
try to 'sudo wlassistant' from the konsole, maybe you can find some hints!

---

### Post by arnold0 on 2006-12-21
did nothing

---

### Post by giancarlo76 on 2006-12-21
Did you install ndiswrapper? Depending on the card, you'll need it to properly load its driver. Otherwise you'll only be able to see it, but not to make it work, if I don't get wrong.

---

### Post by arnold0 on 2006-12-21
dont think ndiswrapper is the problem. it was working fine with it a few days ago and it can still display the wireless networks in the area

but for some reason it is giving me errors when I try to connect to WEP networks

does anyone know a way to connect to a wireless network through command line that might help because it might be a problem with network-manager

---

### Post by Progressive on 2006-12-24
I have a similar problem. The only thing I can think of that is left to do is to try ndiswrapper... I would recommend the same for you.

If anyone else has any better ideas, I would like to know.

---

### Post by theorem_hunter on 2006-12-24
i have a similar problem with my uncles wireless linksys card (its usb)

i cant really install the ndiswrapper driver because that pc cant connect to the internet any other way. unless i download the driver & put it on a usb stick & install it like that... but i dont think its a driver issue. ill try it anyway.

this is the ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

rausb1    Link encap:Ethernet  HWaddr 00:14:BF:75:A2:D1  
          inet6 addr: fe80::214:bfff:fe75:a2d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73876 (72.1 KiB)  TX bytes:206154 (201.3 KiB)

thanks

---

