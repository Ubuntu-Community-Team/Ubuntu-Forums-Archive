---
title: "Impossible to boot from cd. What could possibly have gone wrong?"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Citizento on 2009-06-10
I burned Xubuntu 9 image on a cd and tried it on a quite recent windows machine. Everything went smooth and I could try Xubuntu from the live cd without problems. I also choose to control for errors in the cd from the live cd menu and nothing showed up.
Then I took my older Hp notebook (5 years old), formatted it, partitioned it in two and reinstalled windows Xp in one of the partitions with the Windows cd. Finally I wanted to boot from Xubuntu 9 cd but, surprise, the machine can't read it! I tried many times, also thought that the cd reader may not be clean, but my old notebook still can't recognize it! When trying to boot it simply doesn't see it and opens Windows instead, when trying to inspect it from Windows it looks as the cd-dvd unit is empty.. Opening the Bios menu to look for boot order it was the right one..
Has anybody had the same problem? I don't know what to do except from trying the floppy installation (in that case I would have to buy a floppy disc, I don't have one :p).

---

### Post by zeroseven0183 on 2009-06-10
Try to create a USB Startup Disk on another Ubuntu machine (I assume you have others).

However, it seems that that CD-ROM is in bad shape. Try another one.

---

### Post by clive littlewood on 2009-06-10
Hi

Can you try another cd/dvd in the HP machine as this sounds like a hardware problem.

If a different disc works then we can take it from there.

Clive

---

### Post by Citizento on 2009-06-10
Yes the machine is reading other cds, it just doesn't recognize the Xubuntu cd.

I don't think I can boot from a usb drive.. I didn't try but in the boot order I see: cd drive, hard drive, removable devices/floppy disc, built-in lan..

---

### Post by 3rdalbum on 2009-06-10
If you have a bootable USB drive plugged in, it should show up in the boot order list. Assuming your BIOS supports it - if it's a recent machine, you should have no problems.

---

### Post by Citizento on 2009-06-10
Ok, I will try. But it's not recent, it's 5 years old.

---

### Post by clive littlewood on 2009-06-10
Hi

It appears that you have a strange burn on that cd. I have had a cd play on 1 computer and not another with different make of drive.

Can you download and burn (slowly) another cd on the HP machine so you are using the same drive to do both operations ?

Clive

---

### Post by Citizento on 2009-06-10
> **clive littlewood said:**
> Hi

It appears that you have a strange burn on that cd. I have had a cd play on 1 computer and not another with different make of drive.

Can you download and burn (slowly) another cd on the HP machine so you are using the same drive to do both operations ?

Clive

Ok I'm doing this first. Later I'm posting here about what will happen. Thanks for the support.

---

### Post by Citizento on 2009-06-10
> **clive littlewood said:**
> 

Can you download and burn (slowly) another cd on the HP machine so you are using the same drive to do both operations ?

Clive

It works! I burned the image with cdrtfe at near the minimum speed and now the cd is recognized. Thank you very much everybody for your help! :popcorn::popcorn::popcorn:

---

### Post by mcduck on 2009-06-10
> **Citizento said:**
> Yes the machine is reading other cds, it just doesn't recognize the Xubuntu cd.

I don't think I can boot from a usb drive.. I didn't try but in the boot order I see: cd drive, hard drive, removable devices/floppy disc, built-in lan..
Great that you got the disk working, burned CDs can be a bit tricky depending on the maker of the CD and the drive you use, and burning at low speeds does often help to make sure the disk will work on all drives.While small reading errors might not be that big issue for disks containing music or photos, it definitely is for operating system install disks..

Anyway, I just felt I should mention that the "removable devices"-boot option will most likely boot from USB drives (as there aren't that many other removable devices that could be used for booting..). Just in case you'll need that option some day. :)

---

### Post by clive littlewood on 2009-06-10
Hi

Glad we could help.       Enjoy your Ubuntu    :D


Clive

---

