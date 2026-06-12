---
title: "Please help with Wireless"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by joham524 on 2009-01-08
I just installed Ubuntu and love it! But one thing I need to be able to use Intel Pro set wireless. I need to be able to access a wireless network that is 802.1X and WEP authentication. Where can I find the driver for Pro set?

---

### Post by melojo on 2009-01-08
Goto applications>accessories>terminal and post the output from the commands below.

```

lspci
sudo lshw -C network
ifconfig
iwlist scan

```

this will give us more info!

---

### Post by joham524 on 2009-01-08
lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by melojo on 2009-01-08
sorry wrong link

---

### Post by jdelasalas on 2009-01-08
What kind of laptop do you use?

---

### Post by joham524 on 2009-01-08
Dell XPS M1330

---

### Post by jdelasalas on 2009-01-08
Have you tried the ndiswrapper route with installing your wireless drivers?

---

### Post by joham524 on 2009-01-08
no I am brand new to Ubuntu barely getting the swing of it

---

### Post by melojo on 2009-01-08
What version of ubuntu are you using?

---

### Post by jdelasalas on 2009-01-08
You want to get ndiswrapper, cabextract, and some other stuff

sudo apt-get install build-essential ndiswrapper-common cabextract

After that, you would want to locate the Windows XP version of your driver.  In terminal, run cabextract whateverthenameis.exe.  This will pull out all the necessary files.  You want to find the drivername.inf

Back in terminal run sudo ndiswrapper -i /location/of/driver.inf

ndiswrapper -l just to make sure its installed

then i think there is something afterwards like 

sudo ndiswrapper -m

finally 

 sudo modprobe ndiswrapper

This may be a poorly written tutorial.  I install ndiswrapper a lot so I tend to breeze through it.

---

