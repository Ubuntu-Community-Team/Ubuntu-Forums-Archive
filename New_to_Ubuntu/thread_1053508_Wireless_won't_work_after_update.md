---
title: "Wireless won't work after update"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by MrCr0 on 2009-01-28
I got 8.10. Acer Aspire 5315 laptop.

Typing ```
lspci
``` yields

```
aaron@aaron-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
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
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
aaron@aaron-laptop:~$ 
```

I'm an uber noob at the terminal and networking stuff. A while ago, after installing 8.10, I had trouble getting wireless to work. I followed random instructions somewhere that seemed to make the wireless work. I don't even know what I did. I just typed random things in the terminal according to some post (I can't remember which post). It then seemed to work. 

Now, at around 5:30 pm (gmt -5), I installed the newest updates for 8.10. Once all the updates were taken care of, the wireless didn't work all of a sudden. Any ideas? I don't even know where to start as far as getting wireless back. Maybe another update will fix it?

---

### Post by lkraemer on 2009-01-28
I assume that you are using the madwifi drivers......for your
AR242x.  Which means you at some point made a folder which,
hopefully still contains the drivers.

If so, and you updated your kernel......which caused your
Wifi to be non functional.......

Open a Terminal window.......
When a new Kernel has been downloaded DO:

cd madwifi_*
cd madwifi-*
make clean
make
sudo make install
sudo modprobe ath_pci
reboot

ONLY if you are using the madwifi drivers.

Was this the thread you followed?
[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

lkraemer

---

### Post by sylvainrb on 2009-01-28
You might have done so already but I had to activate 2 different drivers for my wireless to actually work... Just in case!

---

