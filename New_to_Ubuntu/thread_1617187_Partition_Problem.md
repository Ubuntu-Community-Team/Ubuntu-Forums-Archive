---
title: "Partition Problem"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Juiceman17 on 2010-11-09
I just started dual booting Ubuntu 10.10 with windows xp a couple days ago. Everything was going fine until I decided to give ubuntu more room to run by changing the partition size. I attempted to download a copy of Partition Magic while in the windows OS. As soon as I attempted to install the file, the computer shut down. Any time that I try to start windows back up again it gets to the windows screen and shuts off. I can still access all of the files within Ubuntu, but I cannot access windows directly. Any help on how to possibly restore windows would be greatly appreciated.

---

### Post by bioterror on 2010-11-09
> **Juiceman17 said:**
> I just started dual booting Ubuntu 10.10 with windows xp a couple days ago. Everything was going fine until I decided to give ubuntu more room to run by changing the partition size. I attempted to download a copy of Partition Magic while in the windows OS. As soon as I attempted to install the file, the computer shut down. Any time that I try to start windows back up again it gets to the windows screen and shuts off. I can still access all of the files within Ubuntu, but I cannot access windows directly. Any help on how to possibly restore windows would be greatly appreciated.

Move all the important files on windows partition to safe with Ubuntu and reinstall Windows. 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Juiceman17 on 2010-11-09
The problem with that is that when I partitioned the drive, it would only let me give 28gigs to Ubuntu. So its already full. Thats why I was trying to change the partitions in the first place. I think I'm going to go into HP pavilion and delete all the unnecessary files and then attempt to move the partition via Gparted. Assuming that works I should then be able to start moving files over and adjusting the partition after every few gigs until I have Ubuntu taking up at least 100gigs. Its only a 160g hard drive, but I'm looking into using Ubuntu full time, so I'm not too worried.

---

### Post by Juiceman17 on 2010-11-09
Ok so I tried doing that and now i've got another problem. I deleted about 10gigs of files on the windows partition, but it wouldnt let me change the size of the partition until I unmounted it. Now that it's unmounted Gparted says that the space is full. And it wont let me mount the os back into the drive. I know this should be really easy, but I'm still new to this

---

### Post by candtalan on 2010-11-09
> **Juiceman17 said:**
> Ok so I tried doing that and now i've got another problem. I deleted about 10gigs of files on the windows partition, but it wouldnt let me change the size of the partition until I unmounted it. Now that it's unmounted Gparted says that the space is full
just a thought - when you delete files, they often go into the wastebin, which does not remove them from the disk, the files remain on the disk. Did you empty the wastebin?

---

### Post by Juiceman17 on 2010-11-09
Yeah I made sure to empty it before checking. The disk utility says that theres plenty of space in the drive, but I cant access it. The computer considers the used space and free space to be one solid block, so it still wont let me adjust the partition without formatting the drive. I still cant access windows either, although I scanned the disk and it says its working fine

---

### Post by Juiceman17 on 2010-11-09
I ended up having to remove windows from the drive completely. How do I go about extending the Ubuntu partition into the free space? It won't let me do it with Gparted or the disk utility.

---

### Post by KIAaze on 2010-11-10
Are you running Gparted from a Live CD?
You can't modify mounted partitions, so you should run it from a Live CD with nothing mounted.
That's how I always did it and I never had problems resizing partitions.

If it still doesn't work, you should try checking your disk for errors.
Have a look at the "badblocks" and "fsck" programs.
ex:
[http://linuxpoison.blogspot.com/2008/01/howto-check-disk-drive-for-errors-and.html](http://linuxpoison.blogspot.com/2008/01/howto-check-disk-drive-for-errors-and.html)
[http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html](http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html)

---

### Post by Juiceman17 on 2010-11-11
Something in the windows partition was infected, but wiping the slate clean got rid of whatever was there. I ended up splitting off some of the hard drive to use as a swap space, and mounted the rest as /Home. Everything is working just fine, and I can run files that are stored in the new partition now. Unfortunately this p.o.s. only has 512mb of ram, so it can't do all that much. Someday I'll get a new cpu, but in the meantime this will work out nicely.
Thanks for the help guys.

---

