---
title: "Problem connecting with Broadcom BCM4328 wireless"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by ruru on 2008-04-12
I have just installed Ubuntu 7.10 (AMD64) on a MacBook (2.4GHz - one of the new ones with the weird hardware!) and have had some issues setting it up. The biggest problem for me is wireless. It uses a Broadcom BCM4328 card. I have installed ndiswrapper and have got it so far that I can see available networks in nm-applet, and can even connect (it shows a signal in the applet bar) but internet doesn't work.
It seems to be connecting to the router (I am running through an Apple Airport base station - this is not the problem as my desktop running Xubuntu 7.10 also connects wirelessly) but I cannot ping the DNS server).

ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr 00:1B:63:BA:85:A9  
          inet addr:10.0.1.170  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4d40:91ea:0:21b:63ff:feba:85a9/64 Scope:Global
          inet6 addr: fe80::21b:63ff:feba:85a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16194029 (15.4 MB)  TX bytes:2009939 (1.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3545 (3.4 KB)  TX bytes:3545 (3.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1E:52:81:F0:26  
          inet6 addr: fe80::21e:52ff:fe81:f026/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:975077 (952.2 KB)  TX bytes:4960 (4.8 KB)
          Interrupt:16 Memory:50500000-50504000 

 

Perhaps interesting is that wlan0 only has an inet6 (no IPv4) address?

That's as far as I've got. Does anyone have any suggestions?

---

### Post by superprash2003 on 2008-04-12
go to System->administration->network .. and browse to your wireless card and in properties.. make sure that DHCP is enabled..sometimes it may not work with roaming mode

---

### Post by ruru on 2008-04-13
I had tried this (my Xubuntu desktop also has roaming disabled - I guess that makes sense for a desktop!) but it still doesn't work. I get a different result from ifconfg though.

ifconfig:

> 
eth0      Link encap:Ethernet  HWaddr 00:1B:63:BA:85:A9  
          inet addr:10.0.1.170  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4d40:91ea:0:21b:63ff:feba:85a9/64 Scope:Global
          inet6 addr: fe80::21b:63ff:feba:85a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1156 (1.1 KB)  TX bytes:6753 (6.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1964 (1.9 KB)  TX bytes:1964 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1E:52:81:F0:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:50500000-50504000 

wlan0:ava Link encap:Ethernet  HWaddr 00:1E:52:81:F0:26  
          inet addr:169.254.6.196  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:50500000-50504000 



---

### Post by adamos on 2008-04-14
try this -> [http://ubuntuforums.org/showthread.php?t=572005](http://ubuntuforums.org/showthread.php?t=572005)

its a write up i made for 4328 cards. uninstall ndiswrapper and any other changes you made and try that.

---

### Post by ruru on 2008-04-16
Thanks for the pointer - I tried the howto, but have not had success. I also tried some variations ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a2669e6253e78a64b66ed1c27e42c1bb8ae43416](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a2669e6253e78a64b66ed1c27e42c1bb8ae43416))  and have tried compiling ndiswrapper but still no luck.
I have the connection to the point that wlan0 is sending and recieving data - but I can't ping the router. I don't really understand what the wireless card is talking to if not the router - but this surely means that the driver is doing _something_? 
I have seen posts by others with 3rd Gen. Macbooks who have got this to work - so it seems to be possible...
Is there any info I can post that would help to pinpoint the problem?

---

