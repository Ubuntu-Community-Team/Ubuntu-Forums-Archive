---
title: "[SOLVED] wireless confusion"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by generollins on 2008-04-10
Hi

I'm currently at work using the wirless in the office on my new linux installation (gOS). I can am online now! via the wireless point in the office which uses WPA. At home I have WEP mainly because i tried configuring WPA but my laptop in windows wouldn't connect into the network. I'm a little confused that i can just login no problem on the wireless in the office and not at home. I have typed in the hex/WEP key correctly and used the right SID. It picks the network up as i can select it in the drop down menu on the network manager, it also picks up all my neighbours networks but it just doesn't seem to work. Can't even log into the router via the usual 192.168.1.1 address either.

anyone any suggestions? I have an Acer 5102WLMI with an Atheros wireless card. The router at home is a Belkin 54G something or other!!

---

### Post by superprash2003 on 2008-04-10
does it connect successfully?if so, please go to the terminal and type ifconfig and post results here

---

### Post by generollins on 2008-04-10
At work it does cos i'm using it now!!! but at home it doesn't.

I don't know how to look and see if its connected successfully. I know i can't access any websites or my router page.

I'll post the results of an ifconfig ASAP

---

### Post by generollins on 2008-04-10
This is what i got from ifconfig

ian@ian-gOS:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:CF:89:8A:CE  
          inet6 addr: fe80::216:cfff:fe89:8ace/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:16:CF:89:8A:CE  
          inet addr:169.254.9.126  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:16:D4:55:0B:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:D4:55:0B:65  
          inet addr:169.254.4.227  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10232 (9.9 KB)  TX bytes:10232 (9.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-89-8A-CE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14227 errors:0 dropped:0 overruns:0 frame:7148
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1590547 (1.5 MB)  TX bytes:4524 (4.4 KB)
          Interrupt:21 


help??

---

### Post by superprash2003 on 2008-04-10
try setting a static ip for your wifi adapter in system->administration->network and then try

---

### Post by generollins on 2008-04-11
no need!! I made the wireless setting under the network manager thing to roaming mode. Once the wireless icon appeared in the top right corner i had a list of networks that i could pick up (which i could do before via the network manager) then i clicked my network and typed in the details and BAM!!!

It took me a while to get it working because the code above suggested the wifi0 was my wireless card and i couldn't configure it under network tools as it said "unknown device".

my gOS is working exactly how i want it to!!

---

