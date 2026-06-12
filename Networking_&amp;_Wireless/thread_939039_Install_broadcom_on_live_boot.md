---
title: "Install broadcom on live boot"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2008-10-05
I just loaded ubuntu 8.04.1 on to a usb drive to boot. It boots fine, but I was wondering how I can make the broadcom driver for wireless load on this live boot? Is it possible?? Come on, I know it gotta be possible!! Anything possible in linux!

---

### Post by Ayuthia on 2008-10-05
> **lsutiger said:**
> I just loaded ubuntu 8.04.1 on to a usb drive to boot. It boots fine, but I was wondering how I can make the broadcom driver for wireless load on this live boot? Is it possible?? Come on, I know it gotta be possible!! Anything possible in linux!

Which Broadcom card do you have?  Can you post the results of lspci -nn?  It should be just a matter of copying the firmware to /lib/firmware, but it all depends on what card you have.

---

### Post by lsutiger on 2008-10-05
Oh, I have the 4401-B0. 
I thought it would be that simple, but the usb drive does not have a /lib/firmware directory. Should I just add it?
Here's there directory listing for the drive:```
autorun.inf            isolinux     README.diskdefines  ubuntu
b43-fwcutter           ldlinux.sys  syslinux.cfg        umenu.exe
broadcom-wl-4.80.53.0  md5sum.txt   ubnfilel.txt        vesamenu.c32
casper                 pics         ubninit             wubi.exe
dists                  pool         ubnkern
install                preseed      ubnpathl.txt

```

---

### Post by lsutiger on 2008-10-09
bump

---

### Post by Ayuthia on 2008-10-09
Is that what the file structure looks like when you look at the USB drive or when it is being used as the OS?  I am thinking that the /lib/firmware directory is compressed in a file.

By the way the 4401 is most likely your wired ethernet and not your wireless.

---

### Post by lsutiger on 2008-11-09
Thats when I look at the drive. And the card is a Broadcom Corporation BCM4311.

Sorry for the late reply. I sorta put the project on the back burner

---

### Post by cariboo on 2008-11-09
Does your wireless device work when running the LiveCD? If so, if you have Intrepid installed there is a utlity to create a usb boot device installed by default, that can create an exact duplicate of the LiveCD.

Jim

---

