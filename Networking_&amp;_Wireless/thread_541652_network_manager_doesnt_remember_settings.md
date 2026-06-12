---
title: "network manager doesnt remember settings"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by guillemsola on 2007-09-03
It happens to me with two laptops where I installed ubuntu Feisty.  One is an ASUS with a ipw3945 card the other it's a VAIO

With a fresh install wifi works great but Network Manager doesn't remember settings. I mean per example that I need to specify a domain name. I do it and it works but when I reboot my computer I loose those settings and I need to retype again every time I want to explore my share's. 

On booth computers avahi says that I have  a local domain invalid. I don't know If this has something to be with my problem.

I read that maybe I have to use wifi-radar instead of network-manager. Well I'm just a bit confused so any suggestions will be great.

Thanks in advance

Here some outputs from my ASUS

[I]**lspci -nn | grep Network**

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

**lspci -nn | grep Ethernet**

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)

**lshw -C network**

  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:f5:b1:d5
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:c800-c8ff iomemory:fe0ff000-fe0fffff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:91:63:de
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fe1ff000-fe1fffff irq:17

**ifconfig**

eth1      Link encap:Ethernet  HWaddr 00:13:02:91:63:DE  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe91:63de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3531 errors:0 dropped:164 overruns:0 frame:0
          TX packets:1692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3207748 (3.0 MiB)  TX bytes:141718 (138.3 KiB)
          Interrupt:17 Base address:0x2000 Memory:fe1ff000-fe1fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26312 (25.6 KiB)  TX bytes:26312 (25.6 KiB)

**iwconfig**

eth1      IEEE 802.11g  ESSID:"cinca"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:13:46:9E:A4:E9   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/100  Signal level=-45 dBm  Noise level=-45 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:164   Missed beacon:0[/I]

---

### Post by guillemsola on 2007-09-04
Ok I investigate without success. I have tried to reconfigure and reinstall network-manager but now I thing that my problem isn't with network manager. I think I have a problem with **network-admin**. 

They are different things but I cannot reconfigure network-admin. It cannot remember my domain name. I have to write it again every time I use my laptop. Maybe the problem is that I have roaming active but I need to connect to various wifi lans.

Thanks.

---

