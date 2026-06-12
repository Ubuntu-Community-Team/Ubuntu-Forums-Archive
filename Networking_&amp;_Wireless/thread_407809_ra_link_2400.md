---
title: "ra link 2400"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by sir_skiner on 2007-04-12
hi.
i have Ra Link 2460 and Ubuntu 6.10. this card should work out of the box, well it doesnt.

```
kamila@kamila-desktop:~$ sudo ifconfig
Password:
lo        Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:2 errors:0 dropped:0 overruns:0 frame:0
         TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0 
         RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

kamila@kamila-desktop:~$ sudo iwconfig
lo        no wireless extensions.

ra0       RT2400PCI  ESSIDff/any  
         Mode:Managed  Channel=1  Bit Rate:11 Mb/s   
         RTS thr:off   Fragment thr:off
         Encryption key:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sit0      no wireless extensions.

```

executing 
```

sudo iwconfig ra0 essid WAT
```
freezes the system. i'm not sure this is corect ssid name, but it's the only one i can think of.

so please if you have any ideas of how to solve this, help.
i'm quite deperate - it's the second card i'm trying to walk my sister through setting it up with no succes so far.

---

### Post by sir_skiner on 2007-04-13
no ideas??

---

