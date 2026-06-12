---
title: "Ubuntu 10.04 Reboot Error After Install"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by psv1120 on 2010-07-28
Hello,

I am currently new to ubuntu. I am planning on installing ubuntu 10.04 for a file server that I will be setting up at home. 

I am installing Ubuntu on a 160GB HDD attached to my computer. I am then planning on using a RAID card attached to the computer via PCI slot. I will then attach five 250GB HDD's to the RAID and making an LVM with those five HDD's. 

I followed the directions through the ubuntu website for creating LiveCD's. 

This is what happened after:

I boot up and this comes up:

Drive 1 not found: Serial ATA, SATA-1
Drive 5 not found: Serial ATA, SATA-5
Strike the F1 key to continue, F2 to run the setup utility

When i press F1, the computer restarts. I have checked the boot order and CD/DVD-ROM is on top. I have also tried to run ubuntu without installing and going through terminal to reinstall GRUB. It said that the GRUB was successfully reinstalled, but now the only thing the computer does is this cycle.

Could anyone please help?

---

### Post by psv1120 on 2010-07-28
Could the message be a result of an internal error in one of the computer components or do I just need HDD's?

---

### Post by psv1120 on 2010-07-29
UPDATE: I factory reset the BIOS. Now it says:

floppy diskette seek failure.
Strike the F1 key to continue, F2 to run the setup utility.

---

### Post by psv1120 on 2010-07-29
Solution:

After reseting factory default, i disabled floppy support. It turns out that somehow RAID was enabled on SATA drives. Once I disabled that, I finally boot to Ubuntu.

---

### Post by jtarin on 2010-07-29
I'm glad you could help....we need more self-service forums. What a wonderful age we live in.:D

---

