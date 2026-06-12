---
title: "Installing Ubuntu to External HD"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by SirVanity on 2011-01-09
I attempted to do this via wubi. The installation completed just fine. But when I attempted to restart boot Ubuntu from my hd it told me that I needed to put in the Windows CD and boot from there, and select repair. 
Below that it said:
File:              \ubuntu\winboot\wubidlr.mbr
Status:          0x000000e
Info:             The selected entry could not be loaded because the application is missing.

Can anyone help me out here?
And when I try to run it from the CD I get another error saying:
Could not boot /dev/loop0

Any idea what I can do here?

---

### Post by SirVanity on 2011-01-10
Can anyone help me out?

---

### Post by SirVanity on 2011-01-10
Not to mention now when I try to run wubi, I get this: 

pyrun.exe No Disk
> There is no disk in the drive. Please insert a disk into drive \Device\Harddisk1\DR1

---

### Post by rg_stephens on 2011-01-10
This sounds familiar. I got out of a similar situation by re-installing GRUB.  I suspect that the bootloader on your HD got messed up during the install. I wish I could be more helpful

---

