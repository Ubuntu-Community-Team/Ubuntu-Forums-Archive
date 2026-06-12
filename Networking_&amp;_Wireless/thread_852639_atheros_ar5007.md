---
title: "atheros ar5007"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by bigrob301 on 2008-07-07
Hi I have a compaq presario f767nr laptop with atheros card chipset 242x I've been struggling the last couple of days to get the wireless to work after numerous attempts to get it to work using madwifi and blakecmartin  and ndiswrapper i finally got it the strange is now I cannot connect using the etho0 the network monitor icon in the tool bar disappeared it's as if wlan0 replaced eth0 can't explain it any better if anyone can help get both working properly i would appreciate it thanks.

eth0      Link encap:Ethernet  HWaddr   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5923 (5.7 KB)  TX bytes:2172 (2.1 KB)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6656 (6.5 KB)  TX bytes:6656 (6.5 KB)

wlan0     Link encap:Ethernet  HWaddr  
          inet addr:192.168.  Bcast:192.168.  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe51:29d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4904120 (4.6 MB)  TX bytes:604778 (590.6 KB)
          Interrupt:19 Memory:f6000000-f6010000

---

### Post by lisati on 2008-07-07
Have a look here:
[http://ubuntuforums.org/showthread.php?t=795984&highlight=atheros](http://ubuntuforums.org/showthread.php?t=795984&highlight=atheros)
[http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+5007+toshiba](http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+5007+toshiba)
[http://ubuntuforums.org/showthread.php?t=846680&highlight=atheros+5007+toshiba](http://ubuntuforums.org/showthread.php?t=846680&highlight=atheros+5007+toshiba)

---

### Post by Ptero-4 on 2008-07-07
My old laptop (a toshiba with an atheros wifi card) worked good with mandriva 2008.1 and sabayon (both using 2.6.24) using madwifi, you may want to try hardy first (since it also have 2.6.24) or if it fails mandriva.

---

### Post by bigrob301 on 2008-07-10
i finally got it to work using this thread [http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158) even after reboot it still worked the only thing left is the wifi light to work properly remains amber when connected or disconnected thanks

---

