---
title: "How to install Ubuntu 11.04 from USB Pendrive"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Albanez39 on 2011-05-19
I'm running on Wondows XP SP3 and I want to install the latest Ubuntu 11.04. 
I've followed the instructions of the Ubuntu download page. I've downloaded the Universal USB Installer, formatted the USB and installed Ubuntu into the Pendrive. I have tried any damn combination in the BIOS Settings, there are actually 4 USB alternatives : USB-HDD, USB FDD, USB Disc and USB Zip. Booting is impossible. It starts Windows normally or gives the possibility to set Safe Mode or Normal Windows. 

I'm really desperate...can someone help me ??

---

### Post by seawolf167 on 2011-05-19
Welcome to the forums!

[LIST]
[*]Redownload the Ubuntu .iso image and [MD5Sum ]("https://help.ubuntu.com/community/HowToMD5SUM")the download to ensure it downloaded properly (ensure you are not using the x86_64 image if your computer is only 32 bit)
[*]Download [UNetbootin]("http://unetbootin.sourceforge.net/"), then write Ubuntu to your flash drive from UNetbootin
[*]Double check (yes again), your BIOS to ensure that not only is USB booting turned on, but it has a higher boot priority than your hard drive
[*]You should also be able to press a function key to get a boot menu during POST then select your USB drive as the boot device (usually [F10] or [F12])
[/LIST]

---

### Post by I2k4 on 2011-05-19
I've found the Ubuntu Live USB via PenDrive instructions bullet proof on two computers that will boot from USB, and useless on an old PC that the BIOS won't permit.  You don't say much about your PC - I think you better be sure the BIOS will support priority booting from a USB thumb drive or else try a burning a CD and booting from that.

---

### Post by pritam_par on 2011-08-19
If you are not able to boot from the pen drive. Then if possible burn the iso image to CD and install it. If you are using the old machine which don't have the CD writer then get the CD burned from any other machine...
_______________________________
[My BLOg about open source]("http://opensource-sidh.blogspot.com/")              :popcorn:

---

