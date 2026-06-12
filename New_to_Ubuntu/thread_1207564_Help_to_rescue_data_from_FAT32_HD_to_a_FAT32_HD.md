---
title: "Help to rescue data from FAT32 HD to a FAT32 HD"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by waznot on 2009-07-08
I need some guidance recovering lost data.

I am confused about gddrescue, ddrescue, and dd_rescue.  Not just the differences, but for which hard drive formats and hard drive sizes I can use them.

I have installed most of what is mentioned in _[COLOR=DarkOrange][DataRecovery]("https://help.ubuntu.com/community/DataRecovery?highlight=%28%5CbCategoryBackupRecovery%5Cb%29")[/COLOR]_ to cover my bases.

I have a partition on my external hard drive called 'FAT305'.  It is formated as FAT32 and is 305GB.  I have lost some of the data on this partition.[INDENT]     /media/FAT305
[/INDENT]I splurged out and bought another external hard drive to which I want to rescue my data. It is called 'MyBook'. It is FAT32 and 1TB in size.[INDENT]     /media/MyBook
[/INDENT]Some instructions on where to go from here would be great.

---

### Post by waznot on 2009-07-09
These are the two Hard Drives. 'FAT305' is the corrupted drive. 'MyBook' is the drive I want to ddrescue (or whatever) to.

---

### Post by lkraemer on 2009-07-09
Well, if I were in your shoes, I'd start by downloading the following ISO's and then burn them to CDR's as DAO and at the slowest speed with
software like K3B.

1.  Clonezilla
2.  SystemRescueCD
3.  UBCD (Ultimate Boot CD)
4.  You may want to purchase Spinrite by Gibson Research, if your data
    is worth more than the cost of the software.

(Testdisk is on either UBCD or SystemRescueCD)

The first thing I would do is boot from the Clonezilla LiveCD and use
Clonezilla to copy that partition to a duplicate partition on your new
drive.  Then I'd remove the original drive for safe keeping until you
are sure you have your data.  Just make sure you don't kill the
original drive.

I'd then boot the LiveCD of UBCD and look for Testdisk.  Or, maybe it
is on SystemRescueCD.  When you locate it, run Testdisk and let it try to
recover the data.  It will search the drive, and then want to go deeper.
Finally it should ask you if you want to save/copy the data etc.
(If you mess up the disk copy it again with Clonezilla and start over.)

You should end up with your data recovered, or most of it.

Spinrite will do the same, but isn't free.  Older versions of Spinrite
would only do IDE drives, but now they will do SATA.  Not sure about USB
External types.

lk

---

### Post by waznot on 2009-07-10
I have testdisk 6.10-1 already installed, so does that mean I don't have to download  SystemRescueCD and Ultimate Boot CD?

---

### Post by lkraemer on 2009-07-10
Well, you don't have to download them if you have Testdisk, but
I would still download Clonezilla. Then proceed, slowly making
sure of what you are copying and to where.

lk

---

### Post by waznot on 2009-07-10
So I can copy two hundred and something MB to a fat drive?

---

