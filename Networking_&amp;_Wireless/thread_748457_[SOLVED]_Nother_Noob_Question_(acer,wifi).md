---
title: "[SOLVED] Nother Noob Question (acer,wifi)"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by scraghty604 on 2008-04-07
Hi thanxs for the help keep replys to stupid as i have just switched form windows and not to sure how this works

comp is a acer 5570z (5570-2094)

not sure on what i have for a wireless card other then it worked in windows

i seen on other post this so here u go i did it on mine, once again thanxs for the help and keep replys to easy as i would like to keep using this but im this close to goign back to windows :( 

scotty@scotty-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by scraghty604 on 2008-04-07
scotty@scotty-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by pseudo-random on 2008-04-07
It's third from the bottom. Atheros chipset.
Search for a guide on setting up your atheros card in ubuntu.

---

### Post by cdenley on 2008-04-07
I'm not a wireless user, but if I remember correctly, most wireless cards can easily be configured using the network applet in the top-right of your screen. Have you tried this yet?

---

### Post by scraghty604 on 2008-04-07
theres not even the option to wireless.. the only connections are "wired" and "modem"

---

