---
title: "NIC not staying on when sleep or powered down."
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by tomtalk24 on 2015-11-30
Hi all, 

I'm having a problem with my ethernet port turning off when I suspend or hibernate or sleep. So I have wol enabled in the bios, it has worked in the past with Windows. But now I'm using the computer as a data/mail server, I have Ubuntu MATE installed with ethtool. I cant work out why when the system powers down the OS turns the NIC off with it. As you can tell its causing me some frustration.
I have tried and checked some things, but may be missing something. I have poked my nose in pm-utils but cant see anything that would turn it off during power down. My understanding was its just hardware based.

Anyway some help would be greatly appreciated. Kindest regards.

---

### Post by tgalati4 on 2015-12-01
Welcome to the forums.

Install *acpitool* and take a look.  Open a terminal:

```
sudo apt-get install acpitool
acpitool -w
```

Turn on the power to the part of the bus that hosts the NIC with the -W switch:  (go from disable to enable)

Find the slot of the NIC card with *lspci*:

```
lspci
```

```
sudo acpitool -W 5
```

Change the number to match the slot in the first command.

---

### Post by tomtalk24 on 2015-12-02
Hi, thank you for your response and time. 

I'm afraid I'm still having problems. I have been working on it but cant work it out. If I run lspci my Ethernet is 02:00.0, if I run acpitool -w no device is numbered 2. I have checked lsusb also. is there anything else I can try? 

Thanks.

---

### Post by tgalati4 on 2015-12-02
Post both the output of *acpitool -w* and *lspci*.

---

### Post by tomtalk24 on 2015-12-02
tom@Toms-Server:~$ acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. PCI0      S5    *disabled  no-bus:pci0000:00
  2. PEX0      S5    *disabled  pci:0000:00:1c.0
  3. PEX1      S5    *disabled  pci:0000:00:1c.1
  4. PEX2      S5    *disabled
  5. PEX3      S5    *disabled
  6. PEX4      S5    *disabled
  7. PEX5      S5    *disabled
  8. HUB0      S5    *disabled  pci:0000:00:1e.0
  9. UAR1      S5    *disabled
  10. UAR2      S5    *disabled
  11. USB0      S3    *enabled   pci:0000:00:1d.0
  12. USB1      S3    *enabled   pci:0000:00:1d.1
  13. USB2      S3    *enabled   pci:0000:00:1d.2
  14. USB3      S3    *enabled   pci:0000:00:1d.3
  15. USBE      S3    *enabled   pci:0000:00:1d.7
  16. AC97      S5    *disabled
  17. AZAL      S5    *disabled

#######

tom@Toms-Server:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)

I have seem on another forum someone found it to be Ubuntu with my particular Ethernet chip, so booted to the Linux Mint live CD that suspended and wol without issue. He was looking to try to replicate settings but it didn&#8217;t look like it worked for him.

 Thanks again, if all fails I have a few more distos I am familiar with, Ubuntu is just the best with security in my case.

---

### Post by tomtalk24 on 2015-12-04
I have installed 14.04 Ubuntu, it seems this is keeping the NIC on when sleeping and wol without doing anything. Horray. I am curious if this is working because it has named my NIC Eth0 and not Eth0(something)20 like in MATE? Would I have needed to rename it, could that possibly be the problem? More testing. 

I will likely keep posting to this for future people in the same shoes.

---

