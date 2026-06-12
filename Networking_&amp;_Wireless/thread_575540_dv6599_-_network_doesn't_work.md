---
title: "dv6599 - network doesn't work"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by ewel on 2007-10-14
first - I still have some problems with english language, sorry about that

second - installed ubuntu 6.10 on ma hp pavilion dv6599, with noapic nolapic opitons, had some problem with network - my internet provider uses mac address + dhcp - on windows vista changed MAC address (to this from old Network Interface Card) and it works. on ubuntu I'd had problems but now MAC is ok, card receives correct ip, mask, gate and dns. I can see that some packages are sending and receiving but internet still doesn't work, if I try commend 'ping' anythimg (using ip or domain's name) I get:
**From (moje ip) icmp_seq=1 Destination Host Unreachable**
 please someone help me, I can't stand Vista :(

---

### Post by noob12 on 2007-10-14
Can you ping your gateway?

Can you extract and post the output of 
```

ifconfig -a

route -n

```

---

### Post by ewel on 2007-10-14
can't ping gateway

ifconfig -a:
```

eth1      Link encap:Ethernet  HWaddr 00:1B:77:BC:E6:DB  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2224 errors:0 dropped:361 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xe000 Memory:f4000000-f4000fff 

eth2      Link encap:Ethernet  HWaddr 00:16:E6:33:A5:2B  
          inet addr:213.134.181.102  Bcast:213.134.183.255  Mask:255.255.252.0
          inet6 addr: fe80::216:e6ff:fe33:a52b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43222 (42.2 KiB)  TX bytes:6576 (6.4 KiB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

routne -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.134.180.0   0.0.0.0         255.255.252.0   U     0      0        0 eth2
0.0.0.0         213.134.183.254 0.0.0.0         UG    0      0        0 eth2

```

---

### Post by ewel on 2007-10-14
one more thing:

sudo ethtool eth2 says:
```
no data available
``` 

is it normal?

---

### Post by noob12 on 2007-10-14
A few drivers don't have proper ethtool support, but most do.  It is normal for the drivers that don't have proper ethtool support.  

What is the type of device and driver?
```

lscpi -nn

sudo lshw -C network

```

Is the subnet mask  255.255.252.0  correct?

---

### Post by ewel on 2007-10-14
mask is correct - same found on windows, other things I'm going to check in a miniute

---

### Post by ewel on 2007-10-14
lspci -nn:
```

00:00.0 0600: 8086:2a00 (rev 0c)
00:01.0 0604: 8086:2a01 (rev 0c)
00:1a.0 0c03: 8086:2834 (rev 03)
00:1a.1 0c03: 8086:2835 (rev 03)
00:1a.7 0c03: 8086:283a (rev 03)
00:1b.0 0403: 8086:284b (rev 03)
00:1c.0 0604: 8086:283f (rev 03)
00:1c.1 0604: 8086:2841 (rev 03)
00:1c.5 0604: 8086:2849 (rev 03)
00:1d.0 0c03: 8086:2830 (rev 03)
00:1d.1 0c03: 8086:2831 (rev 03)
00:1d.2 0c03: 8086:2832 (rev 03)
00:1d.7 0c03: 8086:2836 (rev 03)
00:1e.0 0604: 8086:2448 (rev f3)
00:1f.0 0601: 8086:2815 (rev 03)
00:1f.1 0101: 8086:2850 (rev 03)
00:1f.2 0106: 8086:2829 (rev 03)
00:1f.3 0c05: 8086:283e (rev 03)
01:00.0 0300: 10de:0427 (rev a1)
02:00.0 0280: 8086:4222 (rev 02)
06:00.0 0200: 10ec:8136 (rev 01)
07:09.0 0c00: 1180:0832 (rev 05)
07:09.1 0805: 1180:0822 (rev 22)
07:09.2 0880: 1180:0843 (rev 12)
07:09.3 0880: 1180:0592 (rev 12)
07:09.4 0880: 1180:0852 (rev 12)

```

lshw:
```

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:bc:e6:db
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:f4000000-f4000fff irq:5
  *-network
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth2
       version: 01
       serial: 00:16:e6:33:a5:2b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r1000 ip=213.134.181.102 multicast=yes
       resources: ioport:c000-c0ff iomemory:f8000000-f8000fff irq:11
  *-usb
       description: Bluetooth wireless interface
       product: HP Integrated Module
       vendor: Broadcom Corp
       physical id: 2
       bus info: usb@5:2
       version: 1.00
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s

```

---

### Post by noob12 on 2007-10-14
This is your card
```
06:00.0 0200: 10ec:8136 (rev 01)
```
which is the 8136.

I don't know much about the r1000 driver; it was phased out in Feisty; that device is handled by the r8169 driver in Feisty.  I don't see any apparently related bugs on the r1000 on launchpad.

There's an off chance you have the same issue as in this thread:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
I'm not very hopeful, but you should try that.

---

### Post by ewel on 2007-10-20
I decided to wait for ubuntu 7,10 - after instalation network is ok :-) thanks for trying to help me

---

