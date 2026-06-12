---
title: "HELP!  Lost wired network connection"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by tra4d on 2008-02-01
I have lost my wired network connection.  Not sure why. Ubuntu (7.10 server ed.) did an update yesterday and that may be it.

I have tried the obvious things - like the cable.  It works.  Checked the settings, they are fine as far as I can tell.  The lights are on on the network 'card' (its an on-board one).  I also installed a second networking card, configured it but that didn't help either.  I also tried the live CD as suggested in some other network lost posts in this forum.

That is about the extent of my knowledge.  Can anyone help?  This is a server we use for VMware and people are needing to connect to it.

Regards,
Scott

---

### Post by jeffus_il on 2008-02-01
Can you post the output of ifconfig?

---

### Post by tra4d on 2008-02-01
> **jeffus_il said:**
> Can you post the output of ifconfig?

Not easily since there is no network connection.

---

### Post by tra4d on 2008-02-01
I will try w/ a usb stick

---

### Post by tra4d on 2008-02-01
> **jeffus_il said:**
> Can you post the output of ifconfig?

Here is the output:
```

eth0      Link encap:Ethernet  HWaddr 00:01:80:10:D5:B3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2      Link encap:Ethernet  HWaddr 00:80:C8:E1:1D:7C  
          inet addr:192.168.7.126  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c8ff:fee1:1d7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:10 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53178 (51.9 KiB)  TX bytes:6634 (6.4 KiB)
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5540 (5.4 KiB)  TX bytes:5540 (5.4 KiB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.7.1  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

---

### Post by tra4d on 2008-02-01
Could this be a motherboard issue since even the live CD didn't work with a second network card installed?

---

### Post by tra4d on 2008-02-01
Anybody?  Something else I can check or post to help diagnose?

---

