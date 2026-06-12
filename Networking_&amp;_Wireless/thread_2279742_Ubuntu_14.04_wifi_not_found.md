---
title: "Ubuntu 14.04 wifi not found"
date: 2015-05-25
forum: Networking &amp; Wireless
---

### Post by chiamin on 2015-05-25
Hi,

I use Ubuntu 14.04 and the wifi worked find. However one day after I disable wireless, the enable wireless option disappeared and never show up again. Now I cannot see any wifi connection. I have follow the thread below but it doesn't work:
[http://ubuntuforums.org/showthread.php?t=2239747](http://ubuntuforums.org/showthread.php?t=2239747)


Would you please help me to regain my wifi? The result of ifconfig is
```

eth0      Link encap:Ethernet  HWaddr 90:e6:ba:45:70:4e  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2605:e000:300f:f400:4cf7:ebe7:df7c:69d6/64 Scope:Global
          inet6 addr: 2605:e000:300f:f400:92e6:baff:fe45:704e/64 Scope:Global
          inet6 addr: fe80::92e6:baff:fe45:704e/64 Scope:Link
          inet6 addr: 2605:e000:300f:f400::1/128 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55631 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:60816510 (60.8 MB)  TX bytes:9129046 (9.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:939261 (939.2 KB)  TX bytes:939261 (939.2 KB)

```

Thank you!

---

### Post by chili555 on 2015-05-25
> Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Do you have the exact same device? If so, you need *firmware-b43-installer.*

If not, tell us what you have:```
lspci -nn | grep 0280
```

---

### Post by chiamin on 2015-05-25
No I don't have the exact same device. The comment "lspci -nn | grep 0280" doesn't give any result.

---

### Post by chili555 on 2015-05-25
> **chiamin said:**
> No I don't have the exact same device. The comment "lspci -nn | grep 0280" doesn't give any result.Since the thread you linked was concerned with how to get that Broadcom working and you haven't that device at all, that's a very good reason why it didn't help!

Let's see:```
lsusb
lspci -nn
```

---

### Post by chiamin on 2015-05-25
I guess you are right. Here are the results:

```

~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 0b05:1751 ASUSTek Computer, Inc. BT-253 Bluetooth Adapter
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)

```

Thank you.

---

### Post by chili555 on 2015-05-25
I'm sorry, I see no wireless device at all. Is it possible it is disabled in the BIOS or, even worse, that it's defective?

---

### Post by chiamin on 2015-05-25
I didn't see it is disable in the BIOS. Maybe it is the worst case, the wireless card is just broken. Thank you very much anyway.

---

