---
title: "Wifi on Toshiba A200-12X"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by corrosion on 2007-07-12
Hi all,

I installed Kubuntu Feisty on a Toshiba A200-12X but wireless doesn't work. I looked into some forums and ndiswrapper is not an option. I looked in other forums too but nothing to get a conclusion to solve. The architecture I use is 64bit. The output of lspci is:



# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 110M / GeForce Go 7300 (rev a1)
04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


We tried with:

modprobe ipw3945
but it doesn't work. The output of iwconfig is:

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Thanks in advance.

---

### Post by sj3fk3 on 2007-07-13
> **corrosion said:**
> Hi all,
04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
Thanks in advance.

It's not going to work, looks like there's no (64 bit?) driver. Are you using the latest kernel?

---

### Post by corrosion on 2007-08-10
I am using the latest kernel I think.

To make it work should I change to i386? Can I use ndiswrapper on 64bit version? I tried but only found driver for vista and didnt work.

Someone can help me please? It is very important.

---

