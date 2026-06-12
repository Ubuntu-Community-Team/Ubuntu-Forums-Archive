---
title: "Wireline/Wireless Dell D610 Network Installation"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by c0reyf on 2007-05-04
Trying to make the new Ubuntu 7.04 install work on my first attempt at Linux. I've read several posts about how to get ndiswrapper (not specifically my card) and install which I'm finding very hard and confusing. My network wireline/wireless aren't recognized by Ubuntu and being a newbie I was hoping that somebody might help me along to at least get a connection on either my wireless or my ethernet jack. I'm running a dual boot XP and Ubuntu Dell D610 laptop with the following information. Any help would be greatly appreciated.


corey@corey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

corey@corey-laptop:~$ lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
corey@corey-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:4F:FC:FA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:11:43:4F:FC:FA  
          inet addr:169.254.10.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2564 (2.5 KiB)  TX bytes:2564 (2.5 KiB)

Thanks 8-)

---

### Post by c0reyf on 2007-05-04
Found my answer in another post.

---

### Post by drega on 2007-05-09
which post?

---

