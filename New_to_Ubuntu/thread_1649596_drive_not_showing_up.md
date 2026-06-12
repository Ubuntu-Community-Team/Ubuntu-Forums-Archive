---
title: "drive not showing up"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by degarb on 2010-12-20
Nautilus isn't showing sdb1.    Even after I terminal sudo mount /dev/sdb1

fdisk -l shows it.

---

### Post by degarb on 2010-12-20
More information: This started happening when I upgraded grub and it recommend I install grub on sdb1 too.  

The drive is cable select, shows up fine in mswindows, and I see error now on boot up 0x000b for sdb.

---

### Post by Hippytaff on 2010-12-20
Can you post the output of the bootscript?
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by degarb on 2010-12-20
"blkid" could not be found.
"fdisk" could not be found.
"filefrag" could not be found.
"losetup" could not be found.
Please install the  missing program(s) and run boot_info_script again.



How do I add proper path to environmental variables.?

---

### Post by Hippytaff on 2010-12-20
Proabably best to boot from a liveCD/USB and download and run the bootscript from there :-)

---

### Post by degarb on 2010-12-20
> **Hippytaff said:**
> Proabably best to boot from a liveCD/USB and download and run the bootscript from there :-)


Would it not be better to add the needed path to the fstab environment variable.

---

### Post by Hippytaff on 2010-12-20
> **degarb said:**
> Would it not be better to add the needed path to the fstab environment variable.

I don't know the correct path, but give it a go :-)

---

