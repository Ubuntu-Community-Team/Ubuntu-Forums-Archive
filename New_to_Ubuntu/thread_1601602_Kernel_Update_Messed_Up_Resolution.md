---
title: "Kernel Update Messed Up Resolution"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by tdrusk on 2010-10-20
Today I did a kernel update to 2.6.32-25-generic and my resolution is wrong. It worked fine in the previous kernel. The correct resolution is not listed in System, preferences, monitors.

My lspci is 
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

```

any ideas?

---

### Post by tdrusk on 2010-10-20
bump :)

---

### Post by NightwishFan on 2010-10-20
Try to remove a xorg.conf if you have one. Run this command in a terminal (case sensitive).

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nwbackup
```

---

### Post by tdrusk on 2010-10-21
> **NightwishFan said:**
> Try to remove a xorg.conf if you have one. Run this command in a terminal (case sensitive).

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nwbackup
```
I didn't have one. Any other ideas?

---

### Post by NightwishFan on 2010-10-21
Create one with:
```
sudo Xorg -configure
```

Then press alt+f2 and type (case sensitive we need the capital X)
```
gksudo gedit /etc/X11/xorg.conf
```

Paste this inside:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Then reboot.

If after reboot it causes problems, boot into recovery mode, choose to open a root prompt, and type:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nwbackup
```

Then reboot again.

---

### Post by tdrusk on 2010-10-26
I tried all of the above and nothing worked. This is pretty frustrating.

Any other suggestions? I believe it has to do with the kernel setting the resolution.

---

### Post by NightwishFan on 2010-10-26
Since the autodetect is not working, try manually adding this stuff to the conf:
```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
        Modes      "1024x768_75.00"
    EndSubSection

EndSection
```

Replace the "1024x768_75.00" with your desired resolutions/refresh-rates. Help here:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Grenage on 2010-10-26
As an addendum to the good advice above, I have a guide [here]("http://www.grenage.com/xorg.html"); it may be of some use.

---

### Post by tdrusk on 2010-10-26
> **NightwishFan said:**
> Since the autodetect is not working, try manually adding this stuff to the conf:
```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
        Modes      "1024x768_75.00"
    EndSubSection

EndSection
```Replace the "1024x768_75.00" with your desired resolutions/refresh-rates. Help here:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Awesome! It worked. Thanks for your help.

I didn't put in the refresh rate and just did 
```
 Modes      "1280x1024"
```
After logging out my resolution was right. I really appreciate it!

> **Grenage said:**
> As an addendum to the good advice above, I have a guide [here]("http://www.grenage.com/xorg.html"); it may be of some use.
Nice. I'll give that a read. 

As I stated above, I did not set the refresh rate. Is there a benefit to different refresh rates or is it a "If it looks fine, use it" kind of thing?

---

### Post by NightwishFan on 2010-10-26
If it was incorrect your monitor would either complain or you would notice it looked grainy.

---

### Post by tdrusk on 2010-10-26
> **NightwishFan said:**
> If it was incorrect your monitor would either complain or you would notice it looked grainy.
Ah I see. Well thanks for your help. :)

---

### Post by tdrusk on 2010-10-26
Darnit! I thought it was working. After a restart it returned to this junky resolution. The xorg.conf has not changed. Any ideas?

---

### Post by tdrusk on 2010-10-26
Update: I followed [this]("http://www.*****************/driver/articles/how-to-change-screen-resolution-after-ubuntu-10-10-installation.html") guide, and jacked a lot of stuff up(couldn't boot into X). So I undid everything that I did and ran ```
sudo update-grub2
```. Now it is back to normal(correct resolution), but I don't know how it is going to behave next time I boot.

---

### Post by NightwishFan on 2010-10-26
Well I hope it works for you. :/

---

### Post by Grenage on 2010-10-27
Why has UF filtered the domain name in the link?

---

