---
title: "No Sound in Pavilon dv3000"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by jose187 on 2009-06-22
I really need help with this.

I have just installed 9.4 on a Pavilon dv3000, and i get NO sound.

All the sound cards have been recognised, but i just get nothing from the computer....

searched high a nd low for a solution, and nothing so far. 

PLEASE HELP!

---

### Post by halitech on 2009-06-22
what is the results of
```
lspci
```and ```
aplay -l
```

---

### Post by jose187 on 2009-06-22
For the *lspci* it is this

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection


For the *aplay -l* its this

> aplay: device_list:217: no soundcards found...


---

### Post by jose187 on 2009-06-23
Please help...anybody :(

---

### Post by halitech on 2009-06-23
there is some info here

[http://ubuntuforums.org/archive/index.php/t-940689.html](http://ubuntuforums.org/archive/index.php/t-940689.html)

from odim31's post:
> open a terminal;
write:
sudo gedit /etc/modprobe.d/alsa-base
give your password when asked;
it's normal that nothing is shown when you are writing your password;
a text document will open;
all you have to do is to past the three lines at the end of the text document;
and finaly reboot your system.
here is the lines of text he refers to
> options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

---

### Post by trivialpackets on 2009-06-23
I had a very similar issue and fix for my DV4.

---

