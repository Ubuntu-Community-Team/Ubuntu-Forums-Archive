---
title: "[SOLVED] Digitus Gigabit PCI Card not working HWaddr FF:FF:FF:FF:FF:FF"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by Archmage on 2007-12-14
I have two network cards in my PC, but I can't get the Digitus Gigabit PCI Card 32Bit, RJ45 10/100/1000 to work in my Ubuntu 7.10. Any help would be highly appricated. I want to point out that I found the HWaddr FF:FF:FF:FF:FF:FF very strange.

```

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr FF:FF:FF:FF:FF:FF  
          inet addr:192.168.10.100  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::fdff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:38654705655 overruns:0 frame:0
          TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x4000 

```

```

dmesg | grep eth0
[   31.787057] eth0: RTL8110s at 0xffffc200005e4000, ff:ff:ff:ff:ff:ff, XID 7cf0f8ff IRQ 20
[   39.070519] r8169: eth0: link up
[   50.619243] eth0: no IPv6 routers present
[  398.580727] NETDEV WATCHDOG: eth0: transmit timed out

```

```

dmesg | grep 8110
[   31.787057] eth0: RTL8110s at 0xffffc200005e4000, ff:ff:ff:ff:ff:ff, XID 7cf0f8ff IRQ 20

```

```

dmesg | grep 8169
[   31.786823] r8169 Gigabit Ethernet driver 2.2LK loaded
[   39.070519] r8169: eth0: link up

```

---

### Post by Archmage on 2007-12-16
I did remove the card and insert a new one. Although it is the same model it works flawless.

I asume that the other card is either broken or the PC just need a cold boot to install it proper.

---

