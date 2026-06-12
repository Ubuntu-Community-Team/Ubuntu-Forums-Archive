---
title: "Unable to install Broadcom BCM43142"
date: 2020-08-26
forum: Networking &amp; Wireless
---

### Post by francescodonoriodemeo on 2020-08-26
[COLOR=#101010][FONT=Ubuntu]Hello everybody,
I have changed the HD of my PC (I installed an SSA). 
After installing Windows and then Ubuntu 20.04, I have a problem with my Broadcom BCM43142. I tried to follow step by step several guide, but I am not able to install the drivers.[/FONT][/COLOR]
[FONT=Ubuntu][COLOR=#101010]I tried to follow this post:
[/COLOR][/FONT]
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

[COLOR=#101010][FONT=Ubuntu]I am in the Specialcase2, that is:[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]Special case #2: Probably only working in 64-bit only. See: [/FONT][/COLOR][https://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](https://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

[COLOR=#101010][FONT=Ubuntu]My PC is an HP-Envy-15, not a Dell. Anyway I have tried, but when I try to install the package I have this message:[/FONT][/COLOR][INDENT]Loading new wireless-bcm43142-6.20.55.19 DKMS files...
Building for 5.4.0-42-generic
Building initial module for 5.4.0-42-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/wireless-bcm43142-dkms.0.crash'
Error! Bad return status for module build on kernel: 5.4.0-42-generic (x86_64)
Consult /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log for more information.
dpkg: error elaborating package wireless-bcm43142-dkms (--configure):
the installed subprocess wireless-bcm43142-dkms script post-installation returned the state of error 10
There have been errors while elaborating
wireless-bcm43142-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]
[COLOR=#101010][FONT=Ubuntu]I am sorry but a part of this quote is a translation, but I think the concept is clear.
I have read also that is necessary to Unable Safe boot, but if I do this, I don't have GRUB and Windows starts.............. [/FONT][/COLOR][IMG]https://forum.ubuntu-it.org/images/smilies/wall.gif[/IMG][IMG]https://forum.ubuntu-it.org/images/smilies/wall.gif[/IMG][IMG]https://forum.ubuntu-it.org/images/smilies/wall.gif[/IMG][IMG]https://forum.ubuntu-it.org/images/smilies/wall.gif[/IMG]
Thank you so much in advance.

---

### Post by chili555 on 2020-08-26
> I tried to follow this post:I wouldn't rely on an eight-year-old post. Eight years is like 300 Linux years. Too much has changed.

With a temporary working internet connection by ethernet, tethering or whatever means possible, open a terminal and do:

```
sudo apt update
sudo apt install bcmwl-kernel-source
```

Reboot and show us:

```
sudo modprobe wl
dmesg | grep -e bcm -e wl
```I don't think it is nearly as difficult as those antique posts make it appear.

---

### Post by francescodonoriodemeo on 2020-08-26
```
sudo modprobe wl[
```
result: ```
modprobe: ERROR: could not insert 'wl': Operation not permittedv
```

```
dmesg | grep -e bcm -e wl
```

result: ```
[    0.000000] DMI: Hewlett-Packard HP ENVY 15 Notebook PC /228D, BIOS F.11 08/07/2014
[    0.771850] integrity: Loaded X.509 cert 'Hewlett-Packard Company: HP UEFI Secure Boot 2013 DB key: 1d7cf2c2b92673f69c8ee1ec7063967ab9b62bec'

```

---

### Post by chili555 on 2020-08-26
I suspect that Secure Boot is the issue. May we please see:

```
sudo apt install mokutil
sudo mokutil –sb-state
```

---

### Post by francescodonoriodemeo on 2020-08-27
I try to translate as regard the first command:

...

mokutil is already updated to the most recent version ((0.3.0+1538710437.fb6250f-1))

This package has been automatically installed and it is not anymore requested: shim

...


As regard the second command, Secure Boot is enabled. But I know that it could be the issue. I wrote that if I disable it, grub doesn't load and windows start...
Maybe you could help me disabling secure boot but there is a way to make Ubuntu or grub start...

---

### Post by chili555 on 2020-08-27
Please check here:  [https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS)

---

### Post by francescodonoriodemeo on 2020-08-27
Thank you very much!!! 
Now I have the problem that Windows starts by default but I think it is ok to manage and solve.
Thank you again!

---

