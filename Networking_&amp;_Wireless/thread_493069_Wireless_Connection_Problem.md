---
title: "Wireless Connection Problem"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by phasee on 2007-07-05
Hi, I am extremely close to fixing this problem, it has come a long way.

I have a wireless network card which I have working in xp so I followed the instruction over at the ndiswrapper wiki site to get these drivers installed in linux.

I followed the instructions all the way and used iwconfig to set everything up.

Before this I was seeing my router but not getting a signal from it, now when I used iwconfig I get a signal sending from the router.

Here is the output from iwconfig:

```
stephen@stephen-desktop:~$ iwlist ra1 scan

ra1       Scan completed :         

 Cell 01 - Address: 00:00:00:BB:00:00                    ESSID:"stewart"                    Mode:Managed
                    Channel:6                   Encryption key:on                   Quality:68/100  Signal level:-54 dBm  Noise level:-256 dBm


stephen@stephen-desktop:~$ iwconfig ra1

ra1       RT61 Wireless  ESSID:"stewart"  Nickname:"stephen-pc"          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:BB:00:00             Bit Rate=54 Mb/s             RTS thr:off   Fragment thr:off          Link Quality=82/100  Signal level:-57 dBm  Noise level:-95 dBm          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Everything is matching, with the Wireless NIC and the router and im receiving a signal as you can see but for some reason I just cannot connect. I have tried without a WEP key.

Output from lspci as follows (might be a bit messy, using win XP atm):

```
stephen@stephen-desktop:~$ lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. VT3351 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0a.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
```

If you need any more info please let me know.
Hope to get this fixed so I can go back to using linux. Thanks.

---

### Post by phasee on 2007-07-05
Hi, does anyone have any suggestions?

Ta.

---

### Post by phasee on 2007-07-06
Surely someone has come across this problem before, I doubt its unique.

Doesn't anyone have a suggestion?

EDIT: ps. I would like to apologise if it seems I am being impatient. The problem is that I now hate having to load Windows. It has gotten to the stage where I would like to make the permanent move to Ubuntu but without the internet I can't as I need it for work and of course play.

If anyone has any ideas which may help I would appreciate it very much. Thanks again.

---

### Post by fredj on 2007-07-06
The above scan of the AP seems to show that encryption is still switched on so I doubt that you will be
able to connect to it without entering a wep or wpa key. Try switching encryption off on the router or
enter the key.

---

### Post by phasee on 2007-07-06
Sorry I should have said I've been using WEP and I've been putting in the key. I've also tried without any protection on the router. 

Still no luck. Thanks again.

---

