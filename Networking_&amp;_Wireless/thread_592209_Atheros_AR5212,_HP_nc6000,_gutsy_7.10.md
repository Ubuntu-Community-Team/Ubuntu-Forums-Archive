---
title: "Atheros AR5212, HP nc6000, gutsy 7.10"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by sandygmaharaj on 2007-10-26
I have nc6000 laptop with Atheros AR5212 wireless chipset. It was working pretty happily even after my upgrade to gutsy gibbon on 18th. But since, the last package update 2-3 days back, it has stopped scanning networks. The card is up, though.

Following are the outputs of various commands:
> sandy@kautilya:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
02:04.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
02:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
02:06.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
02:06.2 System peripheral [0880]: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator [1217:7110]
02:06.3 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
02:0e.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet [14e4:165e] (rev 03)


> sandy@kautilya:~$ dmesg|grep wifi
[   20.868000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   20.868000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.868000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   20.868000] wifi0: mac 5.6 phy 4.1 radio 1.7
[   20.868000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   20.868000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   20.868000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   20.868000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   20.868000] wifi0: Use hw queue 8 for CAB traffic
[   20.868000] wifi0: Use hw queue 9 for beacons
[   20.932000] wifi0: Atheros 5212: mem=0x90080000, irq=11


> sandy@kautilya:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:12:79:3E:1B:AA  
          inet6 addr: fe80::212:79ff:fe3e:1baa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:0D:9D:8E:7C:51  
          inet addr:138.203.250.122  Bcast:138.203.251.255  Mask:255.255.252.0
          inet6 addr: fe80::20d:9dff:fe8e:7c51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22879 errors:1040 dropped:0 overruns:0 frame:0
          TX packets:2403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1040 txqueuelen:1000 
          RX bytes:4797264 (4.5 MB)  TX bytes:528844 (516.4 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi1     Link encap:UNSPEC  HWaddr 00-12-79-3E-1B-AA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:0 (0.0 b)  TX bytes:13294 (12.9 KB)
          Interrupt:11 


But there are no scan results:

> sandy@kautilya:~$ iwlist ath0 scan
ath0      No scan results


Can somebody help?!

---

### Post by karon on 2007-10-29
I think you have to 'sudo' the iwlist command to force a scan ?

---

### Post by root75 on 2007-11-07
i have exactly the same trouble (same hardware)
trouble since last upgrade : scan give no result ..

do you know why there is a wifi0 and ath0 device ?

Thanks

---

