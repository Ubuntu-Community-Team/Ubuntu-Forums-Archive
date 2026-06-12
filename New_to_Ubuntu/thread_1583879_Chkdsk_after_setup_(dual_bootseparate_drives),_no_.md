---
title: "Chkdsk after setup (dual boot/separate drives), no Grub"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by ronkas on 2010-09-28
Hi all,
please be patient and forgive my newbieness.

I've tried to install on my machine Ubuntu 10 in dual boot with my already-installed Windows 7:

the fact is: i want to have W7 on my primary drive and Ubuntu on my second to keep them safely separated.

I trimmed down the ntfs part on the second and created with GParted the ext4 and swap ones, and started the setup specyifing (clicking on "Advanced.." during the wiz) to put the boot loader in sdb (the second drive)
all seems ok, but... i've rebooted and W7 automatically booted and chkdsk with it.

I followed this guide:
**[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)**

What can i do now?


Really TIA.

---

### Post by Paqman on 2010-09-28
Getting chkdsk on an NTFS partition after resizing it is normal, don't worry about that.

I've always just put Grub on the first drive, it may be that if you've put it on the second one you'll need to set that one to boot first.

---

### Post by ronkas on 2010-09-28
Thank you for answering.
I don't know, also in my logic it would be that, but the guide there says specifically to install the grub in the second one, or W7 will screw up the grub fixing the mbr on the first boot drive.

I'm confused: does somebody  has experience of that configuration?
I can't experimenting (at least not now) because I use the related machine for work and I don't want to screw up all

---

### Post by Rubi1200 on 2010-09-28
Hi,
if you have an Ubuntu CD boot the computer choosing to try in live mode.

Then, post the results of the bootscript linked at the bottom of my post.

We also need to know what make of computer/laptop you have and the specifications please.

Thanks.

---

### Post by Paqman on 2010-09-28
> **ronkas said:**
> the guide there says specifically to install the grub in the second one, or W7 will screw up the grub fixing the mbr on the first boot drive.


You only need to worry about that if you're installing Windows after you've already installed Ubuntu. And even if it did, [reinstalling Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") is simple.

---

### Post by ronkas on 2010-09-28
> **Paqman said:**
> You only need to worry about that if you're installing Windows after you've already installed Ubuntu. And even if it did, [reinstalling Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") is simple.

I'm installing Ubuntu AFTER Windows 7, not viceversa.

My conf is amd64 x2 4200+, 2Gb RAM
hd0 sata 300Gb
hd1 sata 200Gb

i will do the livecd/script report soon!

---

### Post by ronkas on 2010-09-28
SOLVED!

It is ok now: was only needed to change hdd boot priority to the drive where's installed grub.

Thank you all folks!

---

### Post by Rubi1200 on 2010-09-28
Glad you got it worked out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

