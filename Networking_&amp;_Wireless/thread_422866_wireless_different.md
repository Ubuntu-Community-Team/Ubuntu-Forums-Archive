---
title: "wireless different"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by cessna_89702 on 2007-04-25
When I run  ```
 lspci | grep Broadcom\ Corporation
```

I get ```
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

```

I had to reinstall Feisty and I had my wireless working fine before but now this tutorial does not work. Altough before they were detecting eth0, eth1,lo, now it detects everything but eth1 && I could click system>networking and have something say wireless before I even installed it and now thats not their either. 

Was it working because eth1 was there?? And if it was how would I get it back so it shows up on iwconfig and is there?

---

### Post by cessna_89702 on 2007-04-25
well i installed the bcm43xx drivers and it got wireless started although its only detecting my neighbors wireless and not mine even though my router is about a foot away.


iwlist scanning gets me 

```
zach@zach-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

```

iwconfig gets me 

```
zach@zach-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```




and ifconfig gets me 

```
zach@zach-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:80:13:B8  
          inet addr:172.16.1.36  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::216:36ff:fe80:13b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:232839 (227.3 KiB)  TX bytes:29734 (29.0 KiB)
          Interrupt:10 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:E2:BB:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6468 (6.3 KiB)
          Interrupt:255 

eth1:avah Link encap:Ethernet  HWaddr 00:14:A5:E2:BB:86  
          inet addr:169.254.9.143  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:255 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:707 (707.0 b)  TX bytes:707 (707.0 b)

```

---

### Post by cessna_89702 on 2007-04-25
never mind i reinstalled and it worked fine again..maybe something went wrong in the 2nd install

---

