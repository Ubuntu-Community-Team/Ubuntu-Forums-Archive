---
title: "wireless connected but no internet wicd"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by malanco on 2008-09-30
hi guys, i dont know why this is happening, my internet connection was working fine, i had a previous version of wicd, but then the update manager told me that there was an update for wicd, so i updated wicd. after that i can connect to any wireless network but i got no internet, just the one that i was connected when i make the update. this is very weird!! :confused: i have a intel 3945 wireless chipset HELP GUYS PLZ!

---

### Post by bibleman on 2008-09-30
run this and post results
```
ifconfig
```

---

### Post by hvacr on 2008-09-30
> **malanco said:**
> hi guys, i dont know why this is happening, my internet connection was working fine, i had a previous version of wicd, but then the update manager told me that there was an update for wicd, so i updated wicd. after that i can connect to any wireless network but i got no internet, just the one that i was connected when i make the update. this is very weird!! :confused: i have a intel 3945 wireless chipset HELP GUYS PLZ!

I have the same problem, WICD does not even run anymore.

---

### Post by malanco on 2008-09-30
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:df:8a:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1b:77:9f:0b:4c  
          inet addr:192.168.2.238  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe9f:b4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5451997 (5.1 MB)  TX bytes:1448396 (1.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91692 (89.5 KB)  TX bytes:91692 (89.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.73.1  Bcast:192.168.73.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.128.1  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-9F-0B-4C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)





now im connected to the only wireless network that i can use :(

---

### Post by bibleman on 2008-09-30
Are there other networks that you want to connect to but you can't? 

It looks as though you have a valid IP address and you should be able to access the internet. It could be an error in the program... I personally have never used it myself, but I might give it a try.

---

### Post by malanco on 2008-09-30
im connected right now to a wireless network and i have working internet, but there are 3 other networks in my office which i can connect it says im connected but i got no internet, i cant ping my router , nothing!, i can use only this network that i am connected, yesterday at my home i have the same issue i associate to the ap but i have no internet, no response :(

---

### Post by malanco on 2008-09-30
anyone?? plz help guys

---

### Post by la3875 on 2008-10-01
:confused: I too saw the upgrade and installed but I think it broke because I can no longer launch the program or connect to networks both wired and wireless. Anyone have any ideas?

Thanks in advance.

---

### Post by imdano on 2008-10-01
> **hvacr said:**
> I have the same problem, WICD does not even run anymore.Read this: [http://wicd.net/latest/changes](http://wicd.net/latest/changes).  If using the update commands to launch the GUI still doesn't work, post here and I'll help you get it working.

---

### Post by malanco on 2008-10-01
ive rolled backed to 1.4.2 and everything worked fine :D , i dont know whats wrong with 1.5 wicd, but ill stick to this version cuz i have no problems . here's the link for those who want to roll back 

[http://downloads.sourceforge.net/wicd/wicd_1.4.2-src.tar.bz2](http://downloads.sourceforge.net/wicd/wicd_1.4.2-src.tar.bz2)

---

### Post by la3875 on 2008-10-02
:D I'm back in the game! If your update broke your wicd like it did mine, i recommend the following solution:

First visit this page [http://wicd.net/punbb/viewtopic.php?id=187](http://wicd.net/punbb/viewtopic.php?id=187) and follow this instruction to uninstall

code: sudo rm /var/lib/dpkg/info/wicd.prerm

Second, open Synaptic and search for wicd and mark for complete removal and apply change

Third, I downloaded the .deb package (**not the .tar**) onto a usb drive and installed and I'm back including my previous wireless profiles!

Hope this helps!

---

### Post by jimmccarthy on 2009-12-22
Hi, i'm fairly new to linux/ubuntu and this morning replaced the default network manager in 9.04 with wicd 1.4.2 (as people said they had had problems with later versions on various forums). I can't connect to the internet with wicd 1.4.2 but can connect to my home network. I have searched the forums and can't find a solution. If anyone can help it would be much appreciated :roll:

---

