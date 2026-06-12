---
title: "Live with Persistence on 2GB Stick"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by I2k4 on 2010-11-24
I took the plunge yesterday to experiment using Ubuntu 10.04 Desktop on my Acer netbook, running LiveCD using the only empty USB memory stick I had, that holds only 2GB.    After learning that Persistence would be needed to save anything, I used the Pendrive installer for the OS and a 1GB container.  All went well and the OS and especially FireFox run well, happy to play with all the little apps that seem to run on first inspection - and it's been stable.

My problem is that after linking up my small DropBox account, all its files installed in the Persistence container and now _I only have about 37MB left.  Then I ran the updater, and found there were about 140MB of system and software updates_ of various kinds, I don't know enough to know what's what.

I stopped the update procedure and came here:  _if I continue and install the updates do they go to Persistence and then stall when it's full? Or do they go into the OS part of the drive, so I would still have my 37MB of Persistence space? _

(I'll look into DropBox to see if I can relocate it somehow on the HDD, or if its Linux version can access my Windows DropBox - that would solve it.)  For now I'm still "playing" but will consider a dual boot or at least a bigger USB drive as time goes on.  Any help appreciated.

---

### Post by lukeiamyourfather on 2010-11-24
Running out of space is not good. Depending on the update, if it runs out of space while updating it could leave it not bootable. I'd suggest getting a larger USB flash drive or try installing it on the computer (or dual boot). Not sure where you live, but in the United States you can get a 16GB USB flash drive for as little as $20.

---

### Post by mastablasta on 2010-11-24
just separate a bit of disk space (i suggest about 20-30GB) and install it there as dual boot. you can experiment from there on, while leaving windows portion of disk intact (except for the main boot record).
 
USB have quite limited write cycles. for little experimenting they are ok, but for a bit more serious use it's better to use hard disk.

---

### Post by I2k4 on 2010-11-24
Thanks for replies - I've literally used the OS for about two hours.  It's running very well as described and I'm happy to poke around on that basis.  But installing updates is part of my "learning process" - I can't seem to learn where exactly the updates would go - the full "Persistence" container is exactly 1GB and there would be room to install updates to software in the OS section of the disk, if that's how it works.  

I didn't find any quick answer about relocating the DropBox at its site.  Regards.

---

### Post by Bucky Ball on 2010-11-24
The updates will update files existing in the operating system partition. This shouldn't add much. If a more efficient way of doing a task is introduced it may even shrink the data. But it is only interested in your system files.

---

### Post by I2k4 on 2010-11-24
Thanks - what I suspected but couldn't be sure.  I'll give the updates a go.

---

### Post by Haedrian on 2010-11-24
> **I2k4 said:**
> I didn't find any quick answer about relocating the DropBox at its site.  Regards.


Right Click on the dropbox symbol> Preferences

The second one under General is "Dropbox Folder Location". Hit the "move" button and select where you want it.

---

### Post by I2k4 on 2010-11-24
As it has finally turned out, moving DropBox was required.  Without that, I got repeated error messages about lack of space, but taking 700MB out of the Persistence container and moving it to the HDD allowed the updates to be installed on the USB drive.  Not sure how the internal partitioning works, but that's what happened.

On this experience, it seems that in my case 4GB is the minimum required to run the Persistence feature effectively on a USB stick.  One of the attractions of keeping it all on a stick would be to plug into just about any PC and have "my" system with FireFox, Dropbox. etc. all in sync.  I have to settle my mind about how to use it, but looking forward to it.

(I'll add a note about using DropBox on the HDD while running the OS on a USB drive.  The DB kept delinking on reboots, very confusing until I found an explanation at DB site:  the time lag between startup for DB and mounting the HDD was causing the issue.  The fix is to disable system startup for DB, and launch it after the HDD is mounted.)

Thanks for all replies.  Have now marked as Solved.

---

### Post by Bucky Ball on 2010-11-24
Please mark thread as 'solved' if it is. :)

---

### Post by C.S.Cameron on 2010-11-25
> Then I ran the updater, and found there were about 140MB of system and software updates of various kinds, I don't know enough to know what's what.

Do not run update on a persistent live install, it will quickly fill your drive and brick it until the casper-rw file is deleted.

The files update manager is meant to update are in a .squashfs file that is read only.

If you need the latest updates, get a larger flash drive and do a full install to it.

---

