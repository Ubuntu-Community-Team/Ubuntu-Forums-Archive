---
title: "quick terminal question dd"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by spiky001 on 2011-05-01
How do I copy using Terminal to a usb stick (sdb) sorry with dd?  (dd if=grub-img.iso of=/dev/sdb1 bs=1440 count=1) When i check sdb1 (usb) nothing is there

---

### Post by The Cog on 2011-05-01
You copied 1440 bytes of something to the start of partition 1 of your stick. You won't see a file on your stick, and may have trashed the fileststem on partition 1.

I'm not sure what you are trying to do, what you are trying to achieve. Can you explain?

---

### Post by Rinzwind on 2011-05-01
> **The Cog said:**
> You copied 1440 bytes of something to the start of partition 1 of your stick. You won't see a file on your stick, and may have trashed the fileststem on partition 1.

I'm not sure what you are trying to do, what you are trying to achieve. Can you explain?
??

bs is blocksize. 

What he wants to do is copy the contents of grub-img.iso to his usb stick.

TS command looks correct. Are you in the directory that has the ISO in it? 

Reference: 
[http://www.linuxfromscratch.org/lfs/view/development/chapter08/grub.html](http://www.linuxfromscratch.org/lfs/view/development/chapter08/grub.html)

---

### Post by matt_symes on 2011-05-01
Hi

> **Rinzwind said:**
> ??

bs is blocksize. 

What he wants to do is copy the contents of grub-img.iso to his usb stick.

TS command looks correct. Are you in the directory that has the ISO in it? 

Reference: 
[http://www.linuxfromscratch.org/lfs/view/development/chapter08/grub.html](http://www.linuxfromscratch.org/lfs/view/development/chapter08/grub.html)

> bs=1440 count=1

TheCog is correct. 1440 bytes copied to sdb1.

@OP why are you trying to copy grub to sdb1 ?

Kind regards

---

### Post by deconstrained on 2011-05-01
OP may be wanting to copy a bootloader to the stick. Problem is, the partition table on the ISO may not work with the stick. It would probably be more reliable to just use fdisk/cfdisk/gparted and grub-install on the stick directly (this all begs the question: where did the ISO come from?)

---

