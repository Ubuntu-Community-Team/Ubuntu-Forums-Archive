---
title: "How to mount cd &amp; cd/dvd drives"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by boxcorner on 2010-03-04
Could someone please tell me what I am doing wrong?
What do I need to do to mount my cd & cd/dvd drives?
I reinstalled Ubuntu 9.10 Desktop Edition from the CD supplied by Ubuntu
now my cd & cd/dvd drives are missing from Places
but they are listed under System > Admin > Disk Utility

CD Drive
GENERIC FREECOM24B
Unknown Size
No Medium Detected
SMART is not available
/dev/sr0

CD/DVD Drive
ATAPI DVD-ROM 16XMax
Unknown Size
No Medium Detected
SMART is not available
/dev/sr1

both drives work fine in Win XP, but not from the Ubuntu GUI

I have tried using Terminal:

/media$ ls
846CA1C66CA1B37A  cdrom  cdrom0  cdrom1  floppy  floppy0

/$ sudo mount /dev/sr0 /media
mount: /dev/sr0: unknown device

/$ sudo mount /dev/sr0 /mnt
mount: /dev/sr0: unknown device

/$ sudo mount -l /dev/sr0 /mnt
mount: /dev/sr0: unknown device

/$ sudo mount /dev/cdrw /media
mount: /dev/sr0: unknown device

/$ sudo mount -l /dev/sr0 /media
mount: /dev/sr0: unknown device

/$ sudo mount -t cdrw /dev/sr0 /media
mount: unknown filesystem type 'cdrw'

/$ sudo mount -l -t cdrw /dev/sr0 /media
mount: unknown filesystem type 'cdrw'

/$ sudo mount -a /dev/sr0 /media
mount: /dev/sr0: unknown device

/$ sudo mount -t cd9660 /dev/cdrw /mnt/cdrw
mount: mount point /mnt/cdrw does not exist

I have read help.ubuntu.com/community/Mount
and tried to find the answer in man 8 mount

I stumbled across a forum thread that mentions fstab
my fstab lists the /, /boot. /home & swap partitions plus
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
however there is no mention of sr0 or sr1

I still don't understand why sr0 isn't recognized, as it is listed by Disk Utility

Can you help please?

---

### Post by mikewhatever on 2010-03-04
Have you tried putting a cd/dvd inside one of the cdroms? According to 'No Medium Detected' there is nothing there.

---

### Post by Paddy Landau on 2010-03-04
> **boxcorner said:**
> ```
/dev/scd0  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0
```
That is the correct entry in your fstab, so that doesn't need changing.

When you put something in the CD or DVD drive, it should auto-mount and you should get an icon on your desktop.

What happens when you insert a CD or DVD (it may take several seconds to mount)?

---

### Post by boxcorner on 2010-03-04
@ mikewhatever  &  @ Paddy Landau
Thank you!  Hmm ... now why didn't I think of that?  
Guess I was expecting to have to mount the drive.
Would have sworn that drive icons appeared in Places, when I installed Ubuntu before.
Must be mistaken as all drives now appear in Places > Computer.
I don't follow the logic of only showing hard drives in Places and not CD drives
Anyway, when I put a disc in either drive & an icon appears on the deskop & in Places.
Here's how this problem started, after reinstalling Ubuntu
I downloaded gparted iso and tried to burn a disc using Accessories > CD/DVD Creator.
Have used Roxio Creator & more recently CDBurnerXP in Win$, but Brasero is unfamiliar to me.
I dragged the downloaded iso file to the CD/DVD Creator window
then clicked on Write to Disc & clicked on Burn as File
am unable to select a disc to which to write.
Message: Please insert a recordable CD or DVD ... etc
but there IS already a blank CD in the drive!
Opening/closing the drive doesn't achieve anything either.
Am using same media that I used in WinXP to create the ubuntu iso for my original installation
so I know the blank disc is compatible with the cd-rw drive.
What do I have to do to get the disc recognized by Brasero?

---

### Post by Paddy Landau on 2010-03-04
> **boxcorner said:**
> Guess I was expecting to have to mount the drive.
The way Linux works, you mount the CD, not the drive. Thus, mounting takes place only after you insert it. I'm glad that's solved!

> **boxcorner said:**
> I don't follow the logic of only showing hard drives in Places and not CD drives
Because it's not mounted. ;)
> **boxcorner said:**
> What do I have to do to get the disc recognized by Brasero?
Firstly, have you tried to erase the disk first with Brasero? That may work.
Secondly, if that doesn't work, try installing [K3B]("apt:k3b") and using that. Sometimes, I find Brasero better for what I want, and other times K3B.

---

### Post by boxcorner on 2010-03-04
@ Paddy Landau
Cheers.  Think I get it now.  Old habits die hard ... Win$ software.
If by erase you mean the Blank option, then Select a Disk > No available disc, is greyed out.
When I tried Eject Disc > Select a disc > CD Drive : The disc in "CD Drive" cannot be ejected, An unknown error occurred.
I tried GnomeBaker, but it kept crashing :-(
Will try K3B ...
_[COLOR=Black]Update[/COLOR]_
Installed K3B, same result, so tried to format the disc, still no joy.
Decided to try different media; inserted disc while looking at the K3B window ...
CD icon suddenly appeared on the desktop, plus a dialog box opened!
Took me a moment to realize it was Brasero, closed K3B - it still wasn't recognizing any disc in drive.
Success with Brasero - data CD successfully burnt.
Well, that was an interesting trial, I mean trail.  I learned a bit more about Ubuntu along the way.
Thank you :-)

---

### Post by Paddy Landau on 2010-03-05
> **boxcorner said:**
> Took me a moment to realize it was Brasero, closed K3B - it still wasn't recognizing any disc in drive.
I think that if you have both open, then only one can get access. But it sounds to me as though your original CD was damaged.

I'm pleased you got it fixed.

---

