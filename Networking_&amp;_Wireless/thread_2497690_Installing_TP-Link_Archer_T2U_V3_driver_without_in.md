---
title: "Installing TP-Link Archer T2U V3 driver without internet"
date: 2024-05-14
forum: Networking &amp; Wireless
---

### Post by grbrust on 2024-05-14
Hi all, I was using archer T2U v3 in my 14.04 and 16.04 system without any issues as the driver was directly provided by TP-Link from their website [https://www.tp-link.com/en/support/download/archer-t2u/#Driver](https://www.tp-link.com/en/support/download/archer-t2u/#Driver) (Kernel version 2.6.18~5.0) . I just had to use **make** command to compile their driver and load it by **sudo insmod 88x2bu.ko** to get the job done.
But recently I upgraded my system and found that direct **make** command don't work from Ubuntu 18.04 onward as it says **make** should be installed first.
So I researched and have already gone through these links like [HTML]https://ubuntuforums.org/showthread.php?t=2456108[/HTML] or [HTML]https://ubuntuforums.org/showthread.php?t=2430134[/HTML] where I'll have go through these steps to get a working internet connection 
```
sudo apt install git dkms
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo make dkms_install
```
but there is a problem as I cannot access internet directly to this PC even by usb tethering as mobile is not allowed here in workplace/my office setup, so my question is can I some how install those packages like **dkms**, **git**, **build-essential**, **linux-headers** from another working machine to this machine? Can I install those packages in offline mode to this to get a stable connection? 
Any help will be appreciated

---

### Post by praseodym on 2024-05-15
Aren't these packages on the Image you installed from? Add the CD/USB as a source

---

### Post by grbrust on 2024-05-15
> **praseodym said:**
> Aren't these packages on the Image you installed from? Add the CD/USB as a source
I had no idea if the Ubuntu installation DVD/USB do contain these packages, if yes then I gonna install them from that. But I'm not getting one thing that if these packages are already in image then why they not get installed in the first place and one more thing that is bothering me is that [COLOR=#0C0D0E][FONT=-apple-system]why themakecommand is working out of the box in 14.04 and 16.04 where as from 18.04 onward distros its not working and saying to install first?[/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system] [/FONT][/COLOR]

---

### Post by morrownr on 2024-05-20
Try this:

[https://github.com/morrownr/8812au-20210820](https://github.com/morrownr/8812au-20210820)

It has documentation.

---

