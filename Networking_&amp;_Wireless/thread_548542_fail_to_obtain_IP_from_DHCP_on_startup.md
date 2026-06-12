---
title: "fail to obtain IP from DHCP on startup"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by Mano[FA] on 2007-09-11
Hi.
My PC with Feisty does not obtain an internet address on startup from the DHCP server. I have to manually rum

```
sudo ifdown eth0
sudo ifup eth0
```

and then it works fine.

It used to work fine before I upgraded to faisty and installed beryl (don't know which caused the problem... could even be something else since I did quite some upgrade all together)

the ifconfig just after startup

```

eth0      Link encap:Ethernet  HWaddr 00:05:5D:78:CB:1E  
          inet6 addr: fe80::205:5dff:fe78:cb1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:564 (564.0 b)
          Interrupt:16 Base address:0xe800
```

and after

```

eth0      Link encap:Ethernet  HWaddr 00:05:5D:78:CB:1E  
          inet addr:192.168.1.198  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe78:cb1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3478379 (3.3 MiB)  TX bytes:548767 (535.9 KiB)
          Interrupt:16 Base address:0xe800
```

any idea???

Thanks a lot in advance

---

### Post by PeterF on 2007-09-11
What does the file  /etc/network/interfaces contain?

For the new network-manager in Feisty the file only has to contain the loopback interface in order to work automatic.
```

auto lo
iface lo inet loopback

```

---

### Post by Mano[FA] on 2007-09-12
thanks! Now it seems to work!!!
which file now contains settings for eth0?

---

