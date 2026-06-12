---
title: "not picking up the wireless network"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by leenuxlee on 2010-09-02
Hello,
I just installed Ubuntu Desktop Edition 32-bit on my Dell Studio 1535 laptop. I generally work with wireless. The computer is no longer even registering that wireless is available. I have tried installing the compat-wireless-2.6.32.16.tar.bz2 but nothing happened.  I also tried installin the Generic complete linux kernel and compat wireless linux modules for version 2.6.32 on x86/x86_64g from the Ubuntu software center. I don't know what to do next.
Thank you for any help you can offer.

---

### Post by silverglade00 on 2010-09-02
Type this command in the Terminal to show which wireless device you have:
```
lspci
```

You can also try to go to System/Adminnistration/Hardware Drivers to see if it has a driver for you. If it doesn't, then post back the results of that command. All it does is type out a list of your internal components on the PCI bus. Be sure to include code tags so it will keep the proper formatting. [ code]Paste the results here.[ /code] but without the spaces inside the brackets.

---

### Post by leenuxlee on 2010-09-02
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```

I have two hardware drivers : Broadcom STA wireless driver (which will not activate: Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log) and ATI/AMD proprietary FGLRX graphics driver.
Thank you.

---

### Post by silverglade00 on 2010-09-02
This page might help you [http://wiki.ubuntu.org.cn/UbuntuHelp:WifiDocs/Driver/bcm43xx](http://wiki.ubuntu.org.cn/UbuntuHelp:WifiDocs/Driver/bcm43xx). Also, could you provide the errors from that log file (/var/log/jockey.log) that it mentioned? It will help locate the problem.

---

### Post by bredman on 2010-09-02
You have the correct driver. The Broadcom STA driver is recommended for BCM4322.

It looks as if the installation of the driver failed. I recommend that you look in the log file mentioned. If you can't find an obvious fault, you could try to paste the contents of the log file. Somebody may recognise the problem.

---

### Post by leenuxlee on 2010-09-02
```
bash: /var/log/jockey.log: Permission denied

```
i'll go and check your link.

---

### Post by bredman on 2010-09-02
Try
sudo cat /var/log/jockey.log
to get around the permission problem

You will be asked for your normal Ubuntu password.

---

### Post by bredman on 2010-09-02
I just noticed that this is a BCM43xx device, and there are a multitude of solutions to get it working.

However, most of the easy solutions depend on you using b43-fwcutter.

At any time, have you used the following command (or anything similar) to install b43-fwcutter on your system? This is normally all that is necessary on a modern computer.
sudo apt-get install b43-fwcutter

---

