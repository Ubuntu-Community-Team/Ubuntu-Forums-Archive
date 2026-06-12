---
title: "Cable unplugged"
date: 2016-04-07
forum: Networking &amp; Wireless
---

### Post by wanght on 2016-04-07
I newly installed my computer with Ubuntu 12.04.4. When I startup the computer, I get one notification of "Network Disconnected - you are new offline".

I have checked the network. The message is shown as following.

```
Wired
cable unplugged
Hardware Address AA:BB:CC:DD:55:66:77:88
IPv4 Address 127.0.0.1
IPv6 Address ::1
Subnet Mask 127.0.0.1
Default Route 127.0.0.1
DNS 127.0.0.1
```

I checked the LAN cable and tried to unplug and plugin for many times. And I also used the same cable to connect to another computer which are installed Windows. It showed that the network cable is OK.

The following message was obtained with the command "ifconfig -a".
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31696 (31.6 KB)  TX bytes:31696 (31.6 KB)
```

Anybody can help me to solve the problem. Thank you very much.

---

### Post by howefield on 2016-04-07
Thread moved to the "*Networking & Wireless*" forum, maybe a better fit.

---

### Post by wanght on 2016-04-07
Furthermore, with the command "sudo pppoeconf", message is obtained:

NO INTERFACE FOUND
Sorry, no working ethernet card could be found.

With the command "lspci -nnk", the result is:
```

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:191f] (rev 07)
 Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
00:01.0 PCI bridge [0604]: Intel Corporation Device [8086:1901] (rev 07)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:a12f] (rev 31)
 Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
 Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Device [8086:a13a] (rev 31)
 Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
00:17.0 SATA controller [0106]: Intel Corporation Device [8086:a102] (rev 31)
 Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
 Kernel driver in use: ahci
 Kernel modules: ahci
00:1b.0 PCI bridge [0604]: Intel Corporation Device [8086:a167] (rev f1)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:a110] (rev f1)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:a118] (rev f1)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:a145] (rev 31)
 Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
00:1f.2 Memory controller [0580]: Intel Corporation Device [8086:a121] (rev 31)
 Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:a170] (rev 31)
 Subsystem: ASUSTeK Computer Inc. Device [1043:86ae]
 Kernel driver in use: snd_hda_intel
 Kernel modules: snd-hda-intel
00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:a123] (rev 31)
 Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
00:1f.6 Ethernet controller [0200]: Intel Corporation Device [8086:15b8] (rev 31)
 Subsystem: ASUSTeK Computer Inc. Device [1043:8672]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:13c2] (rev a1)
 Subsystem: ASUSTeK Computer Inc. Device [1043:853f]
 Kernel modules: nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbb] (rev a1)
 Subsystem: ASUSTeK Computer Inc. Device [1043:853f]
 Kernel driver in use: snd_hda_intel
 Kernel modules: snd-hda-intel
03:00.0 USB controller [0c03]: ASMedia Technology Inc. Device [1b21:1242]
 Subsystem: ASUSTeK Computer Inc. Device [1043:8675]
 Kernel driver in use: xhci_hcd
 
```
Does the OS not recognise the network adapter? Need I install additional driver?

---

### Post by gordintoronto on 2016-04-07
How old is the computer? (New computer, old OS, bad outcome.)

Have you tried 15.10?

---

### Post by wanght on 2016-04-07
It is a new computer. I am using 12.04.4, never tried 15.10

---

### Post by wanght on 2016-04-07
Solved. The version is too old to install in the new computer.

---

