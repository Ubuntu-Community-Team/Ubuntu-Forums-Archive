---
title: "Noob question: How do you find what wireless card you are using?"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by heb1039 on 2008-05-03
I have been slaving away all day, trying to get my wireless working. After much research, trial and error (all errors, actually), I realize that the first thing I needis to figure out which wireless card I am usuing. Alas, I do no know how to find this. Any help?

---

### Post by Ayuthia on 2008-05-03
> **heb1039 said:**
> I have been slaving away all day, trying to get my wireless working. After much research, trial and error (all errors, actually), I realize that the first thing I needis to figure out which wireless card I am usuing. Alas, I do no know how to find this. Any help?
```
lspci -nn
```
This will give you the name and the chipset for your card.  If it is a usb device:
```
lsusb
```

Welcome!!!!

---

### Post by heb1039 on 2008-05-03
Again, being a noob, I want to get this right! 
I get:
> 00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 04)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:03.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
06:03.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller [104c:802e]
06:03.3 Mass storage controller [0180]: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller [104c:ac8f]
06:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
06:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)

Which is it?

---

### Post by prshah on 2008-05-03
> **heb1039 said:**
> I have been slaving away all day, trying to get my wireless working. After much research, trial and error (all errors, actually), I realize that the first thing I needis to figure out which wireless card I am usuing. Alas, I do no know how to find this. Any help?

Why not try my step-by-step guide ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)) to set up your wireless network card? If you run into any problems, post back which step you are stuck at.

---

### Post by heb1039 on 2008-05-03
I get stuck at step number two. 

> 3) Copy your NetGear .INF file (note; the location given here is the most likely; please check your exact location)
Code:

mkdir inf && cp /media/sda1/windows/inf/WG311v3/* inf/


I have no idea where that is, or if I even have it.

---

### Post by prshah on 2008-05-03
> **heb1039 said:**
> I get stuck at step number two. 


Ok what's the output of step #1? Did you find out your wireless card?

---

### Post by heb1039 on 2008-05-03
> gregory@gregory-laptop:~$ lspci | grep -i wireless
gregory@gregory-laptop:~$ lspci grep -i wireless
Usage: lspci [<switches>]

-v		Be verbose
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-b		Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x		Show hex-dump of the standard portion of config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]	Show only selected devices
-t		Show bus tree
-m		Produce machine-readable output
-i <file>	Use specified ID database instead of wireless
-D		Always show domain numbers
-M		Enable `bus mapping' mode (dangerous; root only)
-P <dir>	Use specified directory instead of /proc/bus/pci
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read configuration data from given file
-G		Enable PCI access debugging


Thats was what I got. What it means? I hope you know!

---

### Post by Ayuthia on 2008-05-03
> **heb1039 said:**
> Again, being a noob, I want to get this right! 
I get:


Which is it?
06:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)

---

