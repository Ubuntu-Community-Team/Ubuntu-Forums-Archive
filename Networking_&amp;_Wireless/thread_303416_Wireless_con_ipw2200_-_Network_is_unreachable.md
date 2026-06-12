---
title: "Wireless con ipw2200 - Network is unreachable"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by MaraMax on 2006-11-20
From the Edgy installation my laptop has problem connecting wireless...

I compiled and installed:
kernel  2.6.18.2
ieee80211-1.2.15
ipw2200-1.2.0
ipw2200-fw-3.0

But it can connect.

Some output:

lspci
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)

```
dmesg
```

[   20.192000] ieee80211_crypt: registered algorithm 'NULL'
[   20.328000] ieee80211: 802.11 data/management/control stack, 1.2.15
[   20.328000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.388000] 8139too Fast Ethernet driver 0.9.27
[   20.388000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   20.392000] eth0: RealTek RTL8139 at 0xf01f2c00, 00:13:d4:02:95:ce, IRQ 5
[   20.392000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   20.400000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   20.580000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0
[   20.580000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   20.580000] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   20.580000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   20.992000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

```
ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:12:F0:65:9F:40
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.255
          inet6 addr: fe80::212:f0ff:fe65:9f40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1648 (1.6 KiB)  TX bytes:432 (432.0 b)
          Interrupt:5 Base address:0x4000 Memory:fe8fe000-fe8fefff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1875 (1.8 KiB)  TX bytes:1875 (1.8 KiB)


```
iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"galaxy"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:23:CD:7F
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-33 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
iwlist eth1 scanning
```

eth1      Scan completed :
          Cell 01 - Address: 00:04:ED:23:CD:7F
                    ESSID:"galaxy"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 54 Mb/s
                    Quality=94/100  Signal level=-33 dBm
                    Extra: Last beacon: 1932ms ago

```
lsmod|grep ieee
```

ieee80211              50284  1 ipw2200
ieee80211_crypt         6528  1 ieee80211
ieee1394              302648  2 sbp2,ohci1394

```

I think it's all right but it does'nt work!
If i ping the router...
```

ping 192.168.1.254
connect: Network is unreachable
```

So:
It isn't an hardware problem 'cause it works under windowsXp 
It isn't an Edgy kernel problem 'cause I made a custom kernel and the problem hasn't gone.
It isn't (it seems not to be) a setting problem.

Any solution?

---

### Post by MaraMax on 2006-11-20
any solution?

---

### Post by harro0209 on 2006-11-22
The netmask of your eth1 interface looks very strange, I don't think that it is a valid netmask. Try to change it to 255.255.255.0 to allow for a subnet with 254 hosts (so your router and your computer can reside in the same subnet).

Hope this helps !

---

