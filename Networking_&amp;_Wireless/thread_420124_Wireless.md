---
title: "Wireless"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Sicilian on 2007-04-23
Hey,
i did a clean install of feisty 7.04 and
i can't get my wifi stuff to work,i don't detect any wireless network.
I've used network manager,wifi radar ,kwifimanager,...

iwconfig gives me this output

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"test" 
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0 
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i do have the network manager applet in the upper right corner of the screen
also when i creat a new wireless connection i see a signal icon but there's no signal
or a menu with connections to chose from.

any help would be nice ,thx

---

### Post by diafygi on 2007-04-23
I'm new to Linux, and I'm having the same problem. I am using a Sager NP6260 laptop (I highly recommend it!), and Ubuntu Feisty Fawn 7.04 needs to use a restricted driver for the wireless card. For some reason the wireless card is listed as eth1. Why is this? I thought it would be labeled as a wireless card (wlan0 or something). So maybe network manager is thinking that an ethernet connection doesn't need to search for wireless stuff? How can we get our wireless cards working? Has anyone else had this problem?

Here are some commands and results I've run:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:90:F5:54:0A:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:52:B9:1D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 Memory:d0100000-d0100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:276 (276.0 b)  TX bytes:276 (276.0 b)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist eth1 scanning
```

eth1      No scan results

```

I've attached a screenshot of my network stuff. If ya'll need any more info, please let me know. So far everything else has been cake with Feisty. I'm sooo close to making the switch!

---

### Post by Sicilian on 2007-04-24
Yea,i feel your pain ;)

I'm also trying a belkin wireless usb adapter so far no luck again.
Ill keep you informed on any changes.

Ciao

---

### Post by Floppyjoe on 2007-04-24
It might help to know your wireless cards chipsets.
For a Usb device:
```
lsusb
```
and for a PCI device:
```
lspci
```

---

### Post by Sicilian on 2007-04-25
Hi,

this is my lsusb info

Bus 005 Device 002: ID 1799:8051  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

and my lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


Progress,i finaly see wireless connections in my network manager
apparantly my wireless was shut out in bios.
Now i will try and connect to my network.

Laterz...

---

### Post by diafygi on 2007-04-25
here is my lsusb info:

```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

here is my lspci info:

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
04:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
04:01.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

What should I be looking for here? What were you talking about Sicilian when you said your bios had shut you out?

---

### Post by Sicilian on 2007-04-26
Well when you start up,first look in your bios.
My wifi was turned off there,so when i turned it on
i clould see all the networks in the area.
I'm also trying backtrack2 and it looks pretty good.

later...

---

### Post by diafygi on 2007-04-26
I'm glad that it's finally working for you! I don't think that is the case for me, however :( . I am dual booting with windows xp, and the wireless works fine in windows, so I don't think my wireless card has been disabled.

Since you have managed to solve your problem, and mine doesn't seem to be related, I'm going to jump to a new thread with my problem. I'll post later with a follow up. Good luck with Backtrack2!

---

### Post by diafygi on 2007-04-26
I just wanted to let yall know I moved my problem to this thread: [http://ubuntuforums.org/showthread.php?p=2539619](http://ubuntuforums.org/showthread.php?p=2539619)

---

### Post by Sicilian on 2007-04-26
Thx and keep me informed with your problem!

---

