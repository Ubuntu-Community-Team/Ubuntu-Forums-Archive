---
title: "How to install a driver"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by ubunt12 on 2010-11-09
Hi, ive only just got ubuntu, and if i go on System>Admin>Additional drivers there is nothing there
i was wondering if anyone could tell me how to add a driver.

also i need the Terminal commandf to find out what graphics card ive got.

Thanks.

---

### Post by kaldor on 2010-11-09
Use the "lspci" command and you'll get similar to this:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
***01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)***
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


The first step is knowing which card you have.

---

### Post by ubunt12 on 2010-11-09
k thanks, this is the output:
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

how would i install a driver for that??

---

### Post by kaldor on 2010-11-09
From a few searches it looks like this card has caused issues for some people before.

You're positive there's nother listed under System > Administration > Restricted Drivers (forget exact name)?

If not, take a look here:

[http://www.nvidia.com/object/linux-display-ia32-96.43.18-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.18-driver.html)


[Quote=Instructions]Installation instructions: Once you have downloaded the driver, type " sh NVIDIA-Linux-x86-96.43.18.pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X server configuration file. See the README or run 'man nvidia-xconfig' for details on usage and instructions for those wishing to edit their X config file by hand.[/quote]

---

### Post by ubunt12 on 2010-11-09
nope, and when i tried to run that driver in the link this appeared:

Could not open the file /home/bren/Downloads/NVI…nux-x86-96.43.18-pkg1.run.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

---

### Post by kaldor on 2010-11-09
Try this:

```
chmod +x NVIDIA-Linux-x86-96.43.18.pkg1.run
```

then...

```
sudo sh NVIDIA-Linux-x86-96.43.18.pkg1.run
```

---

### Post by ubunt12 on 2010-11-09
chmod: cannot access `NVIDIA-Linux-x86-96.43.18.pkg1.run': No such file or directory

---

### Post by kaldor on 2010-11-09
Where did you download the file to? Is it in the Downloads folder? If so, change into there with "cd Downloads".

Then rinse-repeat the above :)

---

### Post by ubunt12 on 2010-11-09
its in Downloads and i changed into the cd ~/Downloads and tried the command again and the same output is displayed:

chmod: cannot access `NVIDIA-Linux-x86-96.43.18.pkg1.run': No such file or directory

---

### Post by kaldor on 2010-11-09
Double check the file that you downloaded. Then change the name to match.

---

### Post by ubunt12 on 2010-11-09
ive now changed the name to Match.run, should i try the above again?

---

### Post by kaldor on 2010-11-09
> **ubunt12 said:**
> ive now changed the name to Match.run, should i try the above again?

I meant make sure the names Match, but try it :)

---

### Post by ubunt12 on 2010-11-09
oh ok, lol

---

### Post by ubunt12 on 2010-11-09
did both of them commands on Match.run and the output:

ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section       
         INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

what should i do??

---

