---
title: "Any way to get rid of Grub"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by ErrolRay on 2010-06-09
After upgrading from 9.10 on a dual boot with XP, could no longer get XP to boot.  I know it was something I did during the upgrade.  I wiped the disks, and installed an image of the XP drive C I had made earlier.  Windows is back on the drive, but Grub comes up at boot telling me "no such disk".

Is there anyway I can get rid of grub so I can get XP running, then install Ubuntu again as a dual boot?

Any help will be appreciated.

Errol

---

### Post by bhadotia on 2010-06-09
> **ErrolRay said:**
> After upgrading from 9.10 on a dual boot with XP, could no longer get XP to boot.  I know it was something I did during the upgrade.  I wiped the disks, and installed an image of the XP drive C I had made earlier.  Windows is back on the drive, but Grub comes up at boot telling me "no such disk".

Is there anyway I can get rid of grub so I can get XP running, then install Ubuntu again as a dual boot?

Any help will be appreciated.

Errol

Try the following command in the terminal (Applications>Accessories>Terminal):
```
sudo update-grub
```
It should automatically update your grub configuration to point to the new partition on which XP is placed. Reboot and then try to boot Xp again.

---

### Post by halitech on 2010-06-09
see here: [http://support.microsoft.com/kb/314458/EN-US/](http://support.microsoft.com/kb/314458/EN-US/)

---

### Post by crispy_420 on 2010-06-09
Want to get rid of grub and boot ONLY into XP? [fixmbr]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")

---

### Post by HungryOcopus on 2010-06-09
EasyBCD.

It's a program that will get rid of grub (or stop it working) and make it so you boot right into windows. Very simple to use, one button. The FixMBR stuff looked a bit dangerous to me when i had the same problem.

---

### Post by crispy_420 on 2010-06-09
It also would require an original Microsoft XP disc and not an OEM reinstall disc. So for most people that may also be an issue too since Dell, HP, etc. fail to give you the real disc.

But wouldn't EasyBCD require a working, or functional, version of XP running to mod the boot sector of the drive? And getting into XP is an issue right now? Or did I misread that?

Here is a program that provides an ISO you can use to fix the mbr. I have not used this before so I can not comment it's effectiveness. But it would give the an option that does not require booting into XP. [BootMaster]("http://bootmaster.filerecovery.biz/recover_mbr.html")

Also found a guide to do this with Ubuntu LiveCD [here]("http://lifehacker.com/345928/fix-windows-master-boot-record-with-an-ubuntu-live-cd").

Good Luck

---

### Post by crispy_420 on 2010-06-09
Oh forgot to mention this but some of those Windows PE LiveCDs have tools to fix the Windows MBR.

So BartPE, Ultimate Boot CD for Windows and Hirens BootCD to name a few.

---

### Post by ErrolRay on 2010-06-10
Thanks Crispy,

Fixmbr did the trick the second time.

Errol

---

