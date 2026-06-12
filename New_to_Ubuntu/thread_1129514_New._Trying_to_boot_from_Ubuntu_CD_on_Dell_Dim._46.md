---
title: "New. Trying to boot from Ubuntu CD on Dell Dim. 4600"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by durija on 2009-04-18
I made a live CD from the 8.04.2 iso. Easy. I downloaded the Ubuntu pocket guide for install guidance and have been following its steps. Problem is, no matter what I do, my Dell Dimension 4600 (about 5 years old) boots into Windows. I've pressed F this and F that and gotten into every config menu imaginable, but nothing seems to get this box to try to boot off the CD. I must be missing something fundamental. I'm pretty good at figuring things out, but I honestly have no experience with boot records and bios and such, so I'm probably missing something obvious. My searches have gotten me nowehere (obviously) Oh, and I definitely want to keep my XP partition intact if at all possible. So I need help. Any takers?

---

### Post by matrixblue on 2009-04-18
The ISO may be corrupted. Download another copy (I prefer bittorrent for reliability) or use the Shipit service.

---

### Post by matrixblue on 2009-04-18
Sorry I misready your post. Are you getting to the Grub Menu?

You may need to reinstall and make sure that Grub gets installed.

---

### Post by xarquid on 2009-04-18
Have you gone into your BIOS (right when your computer starts up) and changed your boot order to boot from CD first?

This is different from PC to PC. Usually it is pressing a key repeatedly right when your computer is turned on. I have a Dell and the key is "F2." This will bring you into BIOS. Look for a tab on the left about boot sequence, change the sequence from Floppy, Hard Drive, Hard Drive, CD-ROM...or whatever it is to CD-ROM first. This will force it to look at the CD-ROM drive first and attempt to boot from it.

Watch when your PC turns on. It usually indicates the button to press to get into your BIOS to change system options.

---

### Post by aaronp on 2009-04-18
> **durija said:**
> I made a live CD from the 8.04.2 iso. Easy. I downloaded the Ubuntu pocket guide for install guidance and have been following its steps. Problem is, no matter what I do, my Dell Dimension 4600 (about 5 years old) boots into Windows. I've pressed F this and F that and gotten into every config menu imaginable, but nothing seems to get this box to try to boot off the CD. I must be missing something fundamental. I'm pretty good at figuring things out, but I honestly have no experience with boot records and bios and such, so I'm probably missing something obvious. My searches have gotten me nowehere (obviously) Oh, and I definitely want to keep my XP partition intact if at all possible. So I need help. Any takers?

As soon as you turn on the PC there is likely to be a message that says Press XXXX key yo enter setup/bios etc. etc. Online documentation says it is F12 for your model but you need to press it pretty much as soon as the PC has POSTed (jsut after it beeps)

When you go in there you should be able to find something that shows the boot order or 'boot from' device. From these it is likely to currently show one of your hard disk drives. Select this option and see if you can find your CD drive in the list and change it to that.
If you can, then make sure you choose the 'Save settings and Exit' option, the PC should restart and boot from the CD.

Edit: If F12 doesn't work, try the DEL key or the ESC key, I've seen some other sites that say this is the correct BIOS entry key for your model.

---

### Post by nandemonai on 2009-04-18
So you have changed the boot order to be CDROM then HDD in BIOS and still no go? If so yes could be corrupted burn OR you actually burnt the ISO as a file not an image. Big difference. What can you see on the disc when inside Windows?

---

### Post by durija on 2009-04-18
Well, I tried everything. I did the F2 and the F12. I'm pretty sure the CD is good, but I made it on a Mac with Toast. Usually that is foolproof.

Truth is, when someone says "change the BIOS or boot order" my eyes glaze over since I'm not sure what I'm doing.

So I guess that if the CD is no good, the machine will probably skip and go to what it knows? I'll try another method to create the CD and see if that helps. Thanks for the suggestions.

---

### Post by matrixblue on 2009-04-18
The burning may have been good but if the ISO itself was bad then it wouldn't make a difference

---

### Post by aaronp on 2009-04-18
> **durija said:**
> Well, I tried everything. I did the F2 and the F12. I'm pretty sure the CD is good, but I made it on a Mac with Toast. Usually that is foolproof.

Truth is, when someone says "change the BIOS or boot order" my eyes glaze over since I'm not sure what I'm doing.

So I guess that if the CD is no good, the machine will probably skip and go to what it knows? I'll try another method to create the CD and see if that helps. Thanks for the suggestions.

Maybe. If you changed the boot order to boot first from the CD and then second from the hard disk, if it didn't find anything bootable on the CD it would then try booting from the drive.

Essentially in the BIOS you need to select your CD drive as the first boot device. If you are confident that you know how to change it back then change all the other devices in the sequence to CD as well, then if it doesn't boot at all you know it was the CD causing the issue.

---

### Post by durija on 2009-04-19
Thanks for the replies. They really helped me to narrow it down. Here is how it turned out...

I thought there was a problem with my iso or the burn of the CD. I have VMWare Fusion on my Mac, so I decided to try installing there first in a virtual machine, so that boot order on the Windows box wasn't an issue. 

Tried my first CD. CD not recognized at all as something bootable by VMWare.
Downloaded via torrent and created new CD. Same result. Now I'm sure it's the CD.
Burned iso at 4x speed. (Somewhere I read to try this, although I have no idea why it would matter.) Now it is recognized and the install begins. BUT the install hangs with this message:

"Incorrect CD-ROM detected. The CD-ROM drive contains a CD which cannot be used for the installation. Please insert a suitable CD to continue the installation." I wasn't sure if this was a VMWare issue, so time to go back to the Dell. F2 and boot from CD. BINGO, Ubuntu install begins.

So burning the CD at only 4x was the solution.

---

### Post by aaronp on 2009-04-19
Awesome! Convoluted way of getting it done but the result is all that matters...

:D

---

