---
title: "Please help with built-in Atheros AR5005G wireless adapter"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by BlackRoseBud on 2007-10-02
Works properly under windows vista, and I've read where the Atheros AR5005G is supposed to be supported out of the box with Ubuntu 7.04, but it doesn't detect it.  So I tried to use ndiswrapper and it says

[B]netmw13b : driver installed
        device (11AB:1FAA) present[/B]

after I do ndiswrapper -l in a terminal, then I do

[B]sudo depmod -a
  sudo modprobe ndiswrapper[/B]

and get no errors, so I do iwconfig and it shows 

[B]lo        no wireless extensions.
eth0      no wireless extensions.[/B]

and after entering ifconfig and it shows

[B]eth0      Link encap:Ethernet  HWaddr 00:14:0B:34:85:3E  
          inet addr:192.168.1.77  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bff:fe34:853e/64 Scope:Link
          UP BROADCAST RUNING MULTICAST  MTU:1500  Metric:1
          RX packets:26214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27971278 (26.6 MiB)  TX bytes:1618775 (1.5 MiB)
          Interrupt:21 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2964 (2.8 KiB)  TX bytes:2964 (2.8 KiB)[/B]

So any suggestions on getting my adapter to work?  I really appreciate any and all help!!!:KS

---

### Post by j.bunce on 2007-10-03
```
gksu gedit /etc/network/interfaces
```

try adding it into there

---

