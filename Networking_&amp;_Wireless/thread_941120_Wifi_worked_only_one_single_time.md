---
title: "Wifi worked only one single time"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by machinogodzilla on 2008-10-07
Hi!

Right after my first installation of Ubuntu 8.04 I managed to connect to the Internet through my wireless router without any trouble.

After restarting the system it is impossible to connect again despite the fact that in ath0 properties all networks around me can be seen.

The only thing I did before the restart was using the Update Manager that found 150 or so patches which I installed. This obviously makes it the prime suspect in my eyes now.

What is wrong and how to make it right?

```
zenon@HPZenon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:19705  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zenon@HPZenon:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:0a:80:06:ab  
          inet6 addr: fe80::211:aff:fe80:6ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:11:0a:80:06:ab  
          inet addr:169.254.5.21  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0d:9d:8d:ff:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96564 (94.3 KB)  TX bytes:96564 (94.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-0A-80-06-AB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20078 errors:0 dropped:0 overruns:0 frame:21881
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2513017 (2.3 MB)  TX bytes:7506 (7.3 KB)
          Interrupt:5

zenon@HPZenon:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wifi0
       version: 01
       serial: 00:11:0a:80:06:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 03
       serial: 00:0d:9d:8d:ff:45
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.14 latency=64 mingnt=64 module=tg3 multicast=yes
zenon@HPZenon:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] [1002:cbb2] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc PCI Bridge [IGP 340M] [1002:7010]
00:06.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller Audio Device [10b9:5451] (rev 02)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Modem [0703]: ALi Corporation M5457 AC'97 Modem Controller [10b9:5457]
00:09.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
00:0b.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller [1217:7114] (rev 20)
00:0b.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller [1217:7114] (rev 20)
00:0b.2 System peripheral [0880]: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator [1217:7110]
00:10.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:11.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:12.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:12.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:12.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
00:13.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 03)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon IGP 330M/340M/350M [1002:4337]
zenon@HPZenon:~$ uname -m
i686
zenon@HPZenon:~$ dmesg | grep -e ath -e wlan
[   41.391086] ath_hal: module license 'Proprietary' taints kernel.
[   41.545897] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   41.938190] wlan: 0.9.4
[   42.629590] ath_pci: 0.9.4
[   45.688712] ath_rate_sample: 1.2 (0.9.4)
[   75.764373] ath0: no IPv6 routers present

```

---

### Post by willca on 2008-10-07
try this if it even sees your wireless network.

sudo iwlist ath0 scan

---

### Post by machinogodzilla on 2008-10-08
It listed all networks around including mine.

Just to add to the first post, now the light indicating wireless connection blinks from time to time showing that there is a problem, I suppose. On the other hand the network icon on ubuntu desktop indicates that the networking is enabled.

Still no connection...

---

