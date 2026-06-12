---
title: "no internet connection with 7.10"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by linuxnoob40 on 2007-10-27
i upgraded to the newest and greatest ubunu last week and had connection through the whole process i dual boot between windows and ubuntu so i was using windows all week now i want to use my linux partion again and i have no internet connection  though it works fine in windows using the onboard nic is a realtek rtl8139/810x . dont make any sense why i ahve connection through windows but not on linux?

---

### Post by Steve1961 on 2007-10-27
post the output of ifconfig

---

### Post by mike23455 on 2007-10-27
Also have realtek rtl8139/810x with the same problem, I'm newbie to Linux and really don't know how to manual configure...

---

### Post by Steve1961 on 2007-10-27
This link might help

[http://ubuntuforums.org/showthread.php?p=3591860](http://ubuntuforums.org/showthread.php?p=3591860)

---

### Post by linuxnoob40 on 2007-10-27
eth0      Link encap:Ethernet  HWaddr 00:14:85:E5:9B:21  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:14:85:E5:9B:21  
          inet addr:169.254.6.223  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Steve1961 on 2007-10-27
Try this:

sudo dhclient eth0

---

### Post by linuxnoob40 on 2007-10-27
i got nothing i cant even connect to my router when i try 
alias net-pf-10 off ipv6


it says that ipv6 isnt installed


and the other code you gave me says there are no dhcp leases available

---

### Post by GreaseMonkey on 2007-10-27
I have a similar problem with Ubuntu 7.10

ifconfig shows no connection on my wired network. Stupid thing is that my wireless connection sets up every time with no problems. Both connections work fine in XPSP2.

I always found the opposite to that in the past using SuSE and Deb. :)

Doesn't matter what settings I try with the network tools, the wired network ignores me totally :confused: This is the same on both the live CD and the installed partition.

I wouldn't worry normally, but my wired connection is a bit faster than my wireless when I need to copy large files across the network...

---

### Post by linuxnoob40 on 2007-10-27
yes its quite the irritation i may try another network card and see if it helps . im suspecting the on board is failing  anyhow.

---

