---
title: "Unsupported hardware watermark"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by curbuntuforums on 2011-05-12
Hi,
I'm trying to go back to using the LTS and after installing 10.04.2 I get that watermark - which didn't happen with 10.10 maverick or 11.04 natty.  The ATI CCC functions seem to work just fine so I can't see what the problem is.

Graphics card is Radeon HD 4290 integrated with ASUS M4A89GTDpro motherboard.

I take it the driver 10.04.2 is installing not the same as 10.10 and 11.04 were installing?
I'm getting 8.72.11 from the fresh 10.04.2 install.

---

### Post by doas777 on 2011-05-12
the radeonHD drivers in Karmic and prior do not support ATI integrated cards at all, and in Lucid, they started supporting the HD4200 series, but not all models. 

in this case, your best bet is to go to ati.com and download the proprietary linux driver, and install it. you will have to reinstall it after each kernel update, so be aware.

---

### Post by curbuntuforums on 2011-05-12
Thnx. 
I followed this
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)
and Catalyst 11.5 (8.85) is working now.

to re-install it:
use the downloaded package script?
or just re-use those .deb's that were made?
- fglrx-8.850-0ubuntu1_amd64.deb, etc.

---

### Post by curbuntuforums on 2011-05-13
OK, the kernel upgrade from 2.6.32-28 to 2.6.32-31 just happened...
several reboots later I can't see any issue with the video or the driver... 
How does it get broken?  I don't understand.

---

### Post by doas777 on 2011-05-13
the installer compiles and installs modules within the kernel. if you upgrade teh kernel, those changes usually get thrown away and need to be reapplied. glad your not having that issue though. I usually only noticed it when the visual effects stopped working, or on occasion it would boot to a text prompt. I just kept the installer package in my download folder, so it was easy enough to invoke from the cli. thats my only peice of advice; keep the driver installer somewhere you can find it easily later, just in case.

cheers!

---

### Post by curbuntuforums on 2011-05-14
thnx again.

Found this somewhere re: new kernel patches...
In theory, DKMS should automatically install the fglrx kernel module  for your new kernel the first time you boot it. Should you need to  manually install it: 
 $ sudo dkms build -m fglrx -k `uname -r`
$ sudo dkms install -m fglrx -k `uname -r`

---

