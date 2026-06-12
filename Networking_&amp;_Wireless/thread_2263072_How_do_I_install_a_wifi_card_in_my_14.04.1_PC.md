---
title: "How do I install a wifi card in my 14.04.1 PC?"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by lukon on 2015-01-29
I put Ubuntu 14.04.1 64 on my HP media center PC using the process from a CD, and connected to the internet by ethernet cable.

Then I disconnected the ethernet cable and installed an ENCORE Wireless-G PCI Adapter in the computer.

Then I booted back into Ubuntu.

Now what do I do to get the ENCORE adapter working and connected to my existing wifi network?

---

### Post by chili555 on 2015-01-29
The first step is to identify your wireless device. Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by lukon on 2015-01-29
Oh no. I typed that at my terminal prompt and hit return. All I got was another terminal prompt.

Edit------

Oh, wait. I figured out that your | thing means two commands.

Ok. Here's the output of the lspci -nn part:


00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 81)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 81)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300] [1002:5b60]
01:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300 SE] [1002:5b70]
02:01.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
02:03.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) Video Decoder [4444:0016] (rev 01)
02:04.0 Mass storage controller [0180]: Promise Technology, Inc. 20269 [105a:4d69] (rev 02)
02:05.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
02:08.0 Ethernet controller [0200]: Intel Corporation NM10/ICH7 Family LAN Controller [8086:27dc] (rev 01)


The grep 0280 command returns nothing. It just crashes my terminal session.

---

### Post by chili555 on 2015-01-29
Interesting. Your wireless card, generally an 0280 device, identifies itself as 0200, the same as ethernet:>  Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)Your device is only driven by the ndiswrapper method. It is a method to wrap around the Windows XP driver files; usually .inf and .sys.[http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)

Here is a rough guide as to how to proceed, although some elements are outdated, it shows the general process. [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) I can post a streamlined, more accurate guide if you wish. The only reason I haven't done so at the outset is that this is tricky and troublesome to get going correctly. If returning the item for a fully supported device is an option, I recommend it.

I will be pleased to help in either case.

---

### Post by lukon on 2015-02-01
Thanks, chili555. I'm gonna take a break from this issue for awhile. I might instead go for the option to put up a wireless router bridge downstream end, and then do wired connection to this computer from that. That way, I can also get my game systems in the same room on the net.

---

### Post by chili555 on 2015-02-01
> **lukon said:**
> I might instead go for the option to put up a wireless router bridge downstream endA perfectly valid solution. Back in the early days of my Linux journey, when wireless was nearly impossible, I happily used a bridge for many years.

---

