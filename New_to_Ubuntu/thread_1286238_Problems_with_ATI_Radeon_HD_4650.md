---
title: "Problems with ATI Radeon HD 4650"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2009-10-08
Hiya everyone can anyone tell me the .deb packages required for the installation of the none-free fglrx drivers in ubuntu 9.04?

The annoying thing is I had it working once but now gfx just crashes on reboot

I've got:

[COLOR="Green"]dkms_2.0.21.1-0ubuntu3_all
xorg-driver-fglrx_8.600-0ubuntu2_i386
fglrx-amdcccle_8.600-0ubuntu2_i386
fglrx-kernel-source_8.600-0ubuntu2_i386[/COLOR]

and I am sick of it crashing on reboot can anyone tell me what the missing .deb files are as its driving me mad. :-(

---

### Post by Nightstrike2009 on 2009-10-08
For others with this problem, hope its not just me lol.

I powered up my modem connection and it didn't seem to download automatically properly (Just came up with downloading box and did nothing), but apt told me which files to install on the details tab.
 
I have it working now the files needed are listed below (downloaded manually from ubuntu packages/ jaunty);

[COLOR="Green"]dkms_2.0.21.1-0ubuntu3_all.deb
fglrx-amdcccle_8.600-0ubuntu2_i386.deb
fglrx-kernel-source_8.600-0ubuntu2_i386.deb
xorg-driver-fglrx_8.600-0ubuntu2_i386.deb[/COLOR]

Reboot ubuntu before enabling driver in hardware drivers, then reboot again after selecting enable in hardware drivers on second boot up.

Anyhow problem solved

---

### Post by Nightstrike2009 on 2009-10-08
Why it didn't work before is beyond me as no files where missing think i just forgot to reboot after installing files before selecting enable.

---

### Post by nickleus on 2009-10-30
here's what i did to get desktop effects and 3d games working in karmic amd64 with my ATI Radeon HD 4650:
[http://nickhumphrey.net/showthread.php?p=3345](http://nickhumphrey.net/showthread.php?p=3345)

---

