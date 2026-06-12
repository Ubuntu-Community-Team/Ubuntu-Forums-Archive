---
title: "Feisty Wired Connection Problem"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by JJNova on 2007-10-23
:(

Ubuntu claims that I am connected to the wired network, but I can not *ping* 192.168.1.1 (router) nor 192.168.0.1 (modem) and when I do an* ifconfig*, the following is displayed

```
eth0      Link encap:Ethernet  HWaddr 00:19:D1:FD:F0:7D  
          inet6 addr: fe80::219:d1ff:fefd:f07d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6014 (5.8 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:19:D1:FD:F0:7D  
          inet addr:169.254.10.228  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6680 (6.5 KiB)  TX bytes:6680 (6.5 KiB)

```

I'm not exactly what that output means, but as far as I can figure it's telling me that eth0 is assigning a default address for when a connection is not present. Network Manager is set to DHCP.

Any help would be appreciated. Thank you.

---

### Post by ArponerO on 2007-10-23
Hi,

You don't have an IP (v4) address at all. Try running DHCP manually:

```
sudo dhclient eth0
```

If you still have problems, paste down here the output of the previous command.

Good luck!

---

### Post by JJNova on 2008-01-03
Thanks for the reply. Found out my on board ethenet fried. Which sucked since I had just built the PC 3 days prior. Not I have an ethernet card.

Thanks!

---

