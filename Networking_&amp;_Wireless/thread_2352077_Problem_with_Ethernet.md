---
title: "Problem with Ethernet"
date: 2017-02-09
forum: Networking &amp; Wireless
---

### Post by johny800 on 2017-02-09
Hi everyone!
I found my old laptop and i want to start using it again.
  It had Windows XP but i erased disk and installed Ubuntu 16.04.1 LTS (Xenial Xerus) 32bit.
  I have a problem with internet access. Wifi works fine but wired  connection (ethernet cable,which works on the another computer) doesn't  work.

  Thanks in advance.
  Any help will be appreciated.

if config:
```

  enp16s0   Link encap:Ethernet  HWaddr 00:15:60:ba:5b:62  
          inet6 addr: fe80::c684:351e:e28f:b468/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103678 (103.6 KB)  TX bytes:5977 (5.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:65952 (65.9 KB)  TX bytes:65952 (65.9 KB)

```

sudo lshw -C network
```

*-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: enp16s0
       version: 11
       serial: 00:15:60:ba:5b:62
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5751m-v3.29a latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:c8000000-c800ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlp2s4
       version: 05
       serial: 00:16:6f:6a:66:ef
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:c8400000-c8400fff

```

Edit:
Yes of course , you are right Parapan. My bad.

cat /etc/network/interfaces 
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

Edit 2:
I tried:
```

auto enp16s0
iface enp16s0 inet dhcp

```
It didn't worked.

---

### Post by Parapan on 2017-02-09
> **johny800 said:**
> 
  cat: /etc/networking/interfaces: No such file or directory 


I'm a linux noob myself but i believe its /etc/**network**/interfaces unless its different for your setup. Could you post that please.. I can't tell with my limited knowledge if anything is off in the other stats though other than that there is no IPv4 information

---

### Post by SeijiSensei on 2017-02-09
Try adding a stanza to /etc/network/interfaces for the Ethernet device:
```

auto enp16s0
iface enp16s0 inet dhcp

```

That said, you should choose either Ethernet or wifi when connecting to a single router.  Having both connected can lead to routing problems.

---

