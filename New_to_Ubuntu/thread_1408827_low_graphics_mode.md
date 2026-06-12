---
title: "low graphics mode?"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-16
Hardware drivers is not detecting my graphics card and I don't know what it is.  How do I figure out what driver I have and where do I find the driver?

---

### Post by bwhite82 on 2010-02-16
Try this in a command line and post the results here:

> lspci

---

### Post by achase79 on 2010-02-16
Have you have already checked System->Settings->Hardware Drivers?

---

### Post by hortstu on 2010-02-16
> **Soldierboy said:**
> Try this in a command line and post the results here:

sara@saras-desktop:~$ sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf_backup
[sudo] password for sara: 
cp: cannot stat `/etc/x11/xorg.conf': No such file or directory
sara@saras-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

>  Have you have already checked System->Settings->Hardware Drivers? 

yes thanks

---

### Post by bwhite82 on 2010-02-16
Alright, you have an integrated intel graphics device. So, make sure the xorg driver is installed. Search Synaptic for: xserver-xorg-video-intel (and install if not already). Then open a terminal and type in:

sudo cp /etc/X11/XF86Config /etc/X11/XF86Config.old

then:

sudo gedit /etc/X11/XF86Config

Then look for the section that looks similar to this:

> Section "Device"
    Identifier     "Device0"
    Driver         **"nvidia"**
    VendorName     "NVIDIA Corporation"
EndSection

Change the bold item above to "intel". Save and exit the file. Log out of Gnome and see if that solves your problem.

**IMPORTANT**

If the driver fails to work and simply drops you to the command line, simply restore your backup of XF86Config:

sudo cp /etc/X11/XF86Config.old XF86Config

---

### Post by achase79 on 2010-02-16
run this in terminal to see if your driver is loaded:
```
dmesg | grep 845G
```
if nothing comes up run this:
```
sudo modprobe 845G
```
If it says no module available try downloading the linux driver for the intel graphics from intel.

---

### Post by hortstu on 2010-02-16
another problem... the synaptic stuff is installed now too.

sara@saras-desktop:~$ sudo cp /etc/X11/XF86Config /etc/X11/XF86Config.old
[sudo] password for sara: 
cp: cannot stat `/etc/X11/XF86Config': No such file or directory


> **Soldierboy said:**
> Alright, you have an integrated intel graphics device. So, make sure the xorg driver is installed. Search Synaptic for: xserver-xorg-video-intel (and install if not already). Then open a terminal and type in:

sudo cp /etc/X11/XF86Config /etc/X11/XF86Config.old

then:

sudo gedit /etc/X11/XF86Config

Then look for the section that looks similar to this:



Change the bold item above to "intel". Save and exit the file. Log out of Gnome and see if that solves your problem.

**IMPORTANT**

If the driver fails to work and simply drops you to the command line, simply restore your backup of XF86Config:

sudo cp /etc/X11/XF86Config.old XF86Config

---

### Post by hortstu on 2010-02-17
i hate doing this but I'm stuck...

bump

---

### Post by halitech on 2010-02-17
try this
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.cong_back
```
then
```
gksudo gedit /etc/X11/xorg.conf
```

not certain but I think they stopped using xf86config ages ago

---

