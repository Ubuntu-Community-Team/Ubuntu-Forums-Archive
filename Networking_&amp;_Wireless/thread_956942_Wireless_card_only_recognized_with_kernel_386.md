---
title: "Wireless card only recognized with kernel 386"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by amoignes on 2008-10-23
Hey guys,

I've been searching the forums and net in general for a couple of weeks now, and I haven't been able to find anything remotely close. 

Recently, the kernel upgrades have made ubuntu not able to recognize my wireless card. I am currently running hardy heron, but this began happening with the '-16' generic kernel update way back with feisty.

If I boot with the 2.6.20-16-386 my wireless is fine, as it was with feisty. However, with any of the 'generic' kernels, the computer does not recognize that I have wireless at all.

Has anyone else encountered this? What can I do that will fix this?

---

### Post by Ayuthia on 2008-10-23
> **amoignes said:**
> Hey guys,

I've been searching the forums and net in general for a couple of weeks now, and I haven't been able to find anything remotely close. 

Recently, the kernel upgrades have made ubuntu not able to recognize my wireless card. I am currently running hardy heron, but this began happening with the '-16' generic kernel update way back with feisty.

If I boot with the 2.6.20-16-386 my wireless is fine, as it was with feisty. However, with any of the 'generic' kernels, the computer does not recognize that I have wireless at all.

Has anyone else encountered this? What can I do that will fix this?

What is your wireless card?  Can you post the results of lspci -nn?

---

### Post by amoignes on 2008-10-27
Here is the output for input 'lspci -nn' in Terminal

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 16)
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
08:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

---

### Post by amoignes on 2008-11-10
BUMP

Even with the newest kernel release, the problem still hasn't been fixed. 

Furthering the problem, something is wrong with my ethernet port. I have a Sony Vaio VGN-N325E. For some reason it simply no longer recognizes when ethernet is plugged in. I think this is a hardware issue, probably something to do with the motherboard, since it happens in Vista as well as Ubuntu. While I don't expect to find a fix for this, it means that I haven't been able to try to download patches, since I have to do all my searching on the kernel that works, not the one I can test to try to get working.

Anyone? Help?

---

### Post by amoignes on 2008-12-02
BUMP BUMP BUMP BUMP

Even more information, if anyone at all might be willing to help me...

With the newest kernel release, the wireless has begun to act even more strangely. Now, in order to get wireless working, I have to go to the proprietary drivers applet and reauthorize then reauthorize HAL and "Support for Atheros 802.11 wireless LAN Cards" to get the wireless working. It will, also, work if I simply unauthorized then reauthorize the support for Atheros option. This happens still, only in the 386 kernel. Even the newest kernel hasn't fixed anything.

I'm still a huge newb, but I'm thinking that if I can get HAL and the support to appear in the applet, everything will be right in the world again. Does anybody know the terminal commands to get HAL or the support running or restart them?

THANKS!!!

---

