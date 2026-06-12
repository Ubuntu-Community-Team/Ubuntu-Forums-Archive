---
title: "Wireless keyboard and mouse. Keyboard work but mouse doesn´t"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by djole_nisam_ja on 2008-08-16
Hi people,

I have some wireless keyboard and mouse named "Typhoon" art. nr. 40162

They connect to a PC via wireless router with 2 x PS/2 (one for keyboard and other for mouse).

Official manufacturer´s link is [here]("http://www.typhoon.de/de/art.php?p=689&pv=3")

Keyboard works but mouse doesn´t.

What to do?

Thanks in advance

---

### Post by pytheas22 on 2008-08-16
I'm not sure that I can help, but please post:
```

lspci -nn
lsusb
```

and I'll see if I can find something.

---

### Post by djole_nisam_ja on 2008-08-16
> **pytheas22 said:**
> I'm not sure that I can help, but please post:
```

lspci -nn
lsusb
```

and I'll see if I can find something.

```

lspci -nn
```

gives:

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge [1106:3189]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8235 PCI Bridge [1106:b168]
00:0e.0 Communication controller [0780]: Agere Systems LT WinModem [11c1:044e]
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) [1002:5d44] (rev 01)


```

lsusb
```

gives:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
Bus 001 Device 001: ID 0000:0000


but I repeat it´s 2 x PS/2 wireless router (one PS/2 for mouse and other for keyboard)

---

### Post by pytheas22 on 2008-08-16
The manufacturer's site mentions something about the keyboard and mouse having to operate on different radio channels:
> 
Q.Why does the Kit has 2 ID channels?
A. That is because both Keyboard and Mouse are operated via Radio Frequency. Both must be set apart on the Channel ID. That means if the Keyboard is set to Channel "1", the Mouse must be set to Channel "2".

Are you sure they're set to operate on different channels?  Also, have you tested them in a different computer to be sure that the mouse definitely works?

You could also try contacting them ("Ich habe eine weitere Frage" at the bottom of the page) to see if they'll tell you anything about Linux support.

---

### Post by djole_nisam_ja on 2008-08-17
> **pytheas22 said:**
> The manufacturer's site mentions something about the keyboard and mouse having to operate on different radio channels:


Are you sure they're set to operate on different channels?  Also, have you tested them in a different computer to be sure that the mouse definitely works?

You could also try contacting them ("Ich habe eine weitere Frage" at the bottom of the page) to see if they'll tell you anything about Linux support.

Yes, they are on different channels.

Will try

---

### Post by dez93_2000 on 2011-08-17
Hi all, resurrecting an oldie here. Just been given a similar thing - typhoon wireless keyboard & mouse, but it's usb to cradle which wirelessly links to the devices. Same warning about different channels.
Art #: 40700

Keyboard works, mouse doesn't. Is charged up, and optical bit is glowing red so it looks good to go.

Pasted details below:

lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation 82P965/G965 Memory Controller Hub [8086:29a0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82P965/G965 PCI Express Root Port [8086:29a1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller [8086:2810] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller [8086:2820] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller [8086:2825] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 8800 GT] [10de:0611] (rev a2)
03:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
03:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 14)
05:00.0 Mass storage controller [0180]: Promise Technology, Inc. PDC20268 (Ultra100 TX2) [105a:4d68] (rev 02)

lsusb:
Bus 007 Device 003: ID 062a:0107 Creative Labs 
Bus 007 Device 002: ID 1532:000d Razer USA, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0518:0002 EzKEY Corp. EZ-9900C Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I've still got my usb wired keyboard and mouse plugged in. The mouse is the Razer, the keyboard *may be* the EzKey... or the creative labs? It's a saitek keyboard but it's exactly the same actual keyboard as the wireless typhoon branded one.

Does anyone know how I can find out whether they're trying to be on the same channel?
And is having a usb mouse already plugged in likely to cause a problem?
Cheers

Dez

---

### Post by dez93_2000 on 2011-08-17
"And is having a usb mouse already plugged in likely to cause a problem?" - no. Rebooted with neither wired mouse nor keyboard plugged in & wireless keyboard still works and wireless mouse still doesn't.

---

