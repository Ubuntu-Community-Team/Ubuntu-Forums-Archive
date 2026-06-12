---
title: "Booting results in GRUB prompt"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by rp_allen on 2009-03-14
I attempted to install Ubuntu as a dual boot system (with Windows XP already instaled) on my new AspireOne computer. Since it does not have a CD or DVD drive I used an LG external CD/DVD drive.  During the installation process the it "stalled" (got to 15% and didn't go further for more than 15 minutes).  I had to turn the computer off.  When I turned it back on, whether I boted from the hard drive or the external CD/DVD all I got was a Grub prompt.  What can I do?

---

### Post by rp_allen on 2009-03-14
I attempted to install Ubuntu as a dual boot system (with Windows XP already installed) on my new AspireOne computer. Since it does not have a CD or DVD drive I used an LG external CD/DVD drive.  During the installation process the it "stalled" (got to 15% and didn't go further for more than 15 minutes).  I had to turn the computer off.  When I turned it back on, whether I boted from the hard drive or the external CD/DVD all I got was a Grub prompt.  What can I do?

---

### Post by taurus on 2009-03-14
You can boot your machine with windows boot disc and fix the MBR or you can use Super GRUB Disk to remove GRUB from MBR.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by carml on 2009-03-14
Maybe you stopped the installation thinking it was blocked, try to install again the OS.
During the installation process the installer stays stactionary at certains degrees for a while,then restarts. :)

---

### Post by overdrank on 2009-03-14
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by rp_allen on 2009-03-14
I obtained a Super GRUB Disk and it didn't help.  When I booted with this disk I still got GRUB.  I am certain the Super GRUB Disk is working as I used it on a different computer.  Any other ideas? 

> **taurus said:**
> You can boot your machine with windows boot disc and fix the MBR or you can use Super GRUB Disk to remove GRUB from MBR.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by taurus on 2009-03-14
Go into the BIOS and see which device is first on the list as bootable device?

---

### Post by rp_allen on 2009-03-14
When I boot, I hit F12 and then select the CD drive as the boot device.  his worked satisfactorily before I did the failed install.


> **taurus said:**
> Go into the BIOS and see which device is first on the list as bootable device?

---

### Post by taurus on 2009-03-14
Then there is something wrong with the CD that you just burnt.  Do you have another machine that you can test out that CD to see if it boots?  Otherwise, try another disc that you know works to see if your machine can boot from that disc with F12.

---

### Post by rp_allen on 2009-03-14
I tested the CD on another computer and it worked.  I also connected the external CD drive to another computer and it also worked.

> **taurus said:**
> Then there is something wrong with the CD that you just burnt.  Do you have another machine that you can test out that CD to see if it boots?  Otherwise, try another disc that you know works to see if your machine can boot from that disc with F12.

---

### Post by adrian15 on 2009-03-18
> **rp_allen said:**
> When I boot, I hit F12 and then select the CD drive as the boot device.  his worked satisfactorily before I did the failed install.

If you had been able to boot the same disk it only means that it is a bug from your BIOS (I have already seen this, hard disk does not have a correct mbr, and whatever the reason is, no cdrom is able to boot, well I think that sometimes Windows installation disk did boot).

Can you please try if Windows installation disk do boot?

adrian15

---

