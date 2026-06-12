---
title: "Ubuntu on USB HDD"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Neil Purling on 2010-05-10
Yesterday I bought a tiny Asus Eee Super Slim 30Gb USB HDD that fits in your palm.
I installed Ubuntu on it & ran the update (took ages).
Without this device connected I got a error message. I assume this was because it was expected to find GRUB on the USB drive (hdc).
I used a old CD of Super Grub to wipe whatever had been tacked onto the boot area of my C:/ drive, so XP boots as expected.

The desired boot order is: CD-ROM, USB, C:/ drive.
There is a slave, but I don't suppose it is relevant to the boot issue. That was formatted FAT32 so if I added Ubuntu it would be visible.

---

### Post by zkriesse on 2010-05-10
Are you trying to make an External Bootable Drive running Ubuntu?

---

### Post by Neil Purling on 2010-05-10
The drive booted Ubuntu before. However when I shut down and removed the USB drive Win XP did not boot.
It was like the Ubuntu put something on the boot sector of C that referred to GRUB proper on the USB drive.
What I want is for the system to look at the CD-ROM first and then gor to a GRUB splash screen wherein boot Win XP is default after x seconds delay and USB boot being the other option.
Is there a way of installing GRUB with this behaviour?

---

