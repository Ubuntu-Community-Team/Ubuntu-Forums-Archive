---
title: "wireless problem with fujitsu n3500 notebook laptop (hardy)"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by nick_jones on 2008-05-06
i posted this in the beginners forum but didn't get any replies, hopefully  i'll have more luck over here :)

i installed ubuntu 8.04 a few days ago on my laptop and i'm  having trouble connecting to the internet via wifi. i'm able to connect when i have windows xp running. right now i'm using a wired connection, which seems to be working okay.

i'm not sure my exact laptop model, it's a fujitsu, n3500 notebook, i believe. i read a bunch of threads and most said to run lspci in your terminal, here's what came up:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
06:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


```

i'm able to see the wireless networks in my area, but when i try to type in the WEP key and connect it doesn't log me on. i've made sure i'm typing in the right key about 30 times, heh


i read a few more threads and people seem to ask for this information, so here. if you need anything else let me know, thanks



when i type in sudo lshw -c network
```
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

```

when i type in iwconfig (i did this when it was tying to connect to my wireless network)
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"verizon"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:18:01:A2:24:1E   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=-56 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:334  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

```

when i type in lspci -nn
```
owner@owner-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M22 [Mobility Radeon X300] [1002:5460]
06:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
06:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG Network Connection [8086:4223] (rev 05)
06:06.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:06.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:06.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:06.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]

```

---

### Post by Ayuthia on 2008-05-06
06:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG Network Connection [8086:4223] (rev 05)

This is your wireless card.  Can you post your lshw -C network (need the uppercase C instead of the lowercase one).  It will help see which module your wireless is trying to use.

You might try to turn off encryption just to see if you can connect.  It will help determine if you have a problem connecting or have a problem connecting with encryption.

---

### Post by nick_jones on 2008-05-06
> **Ayuthia said:**
> 06:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG Network Connection [8086:4223] (rev 05)

This is your wireless card.  Can you post your lshw -C network (need the uppercase C instead of the lowercase one).  It will help see which module your wireless is trying to use.

You might try to turn off encryption just to see if you can connect.  It will help determine if you have a problem connecting or have a problem connecting with encryption.


okay, here's what i got:

```
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


```

i turned off my encryption, and what do ya know, it's working now :mrgreen:

any idea on how to connect with the encryption on? :)

---

### Post by Ayuthia on 2008-05-06
Sorry, I don't have much experience in troubleshooting encryption.  I have not had a real need for encryption where I live.  You might create another post saying something like "Having Trouble Connecting with WEP/WPA on an Intel 2495abg on Hardy".  I have seen one expert on WEP that has been answering posts during the past few days.

---

### Post by nick_jones on 2008-05-06
> **Ayuthia said:**
> Sorry, I don't have much experience in troubleshooting encryption.  I have not had a real need for encryption where I live.  You might create another post saying something like "Having Trouble Connecting with WEP/WPA on an Intel 2495abg on Hardy".  I have seen one expert on WEP that has been answering posts during the past few days.
cool, thanks a lot for all the help :grin:

---

