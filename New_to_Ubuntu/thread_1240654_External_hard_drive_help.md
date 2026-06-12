---
title: "External hard drive help"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by jalehtor on 2009-08-14
LONG story. I have a desktop with 40gb hard drive. At the moment, I'm using about 17gb of that hard drive. I wanted to dual format it with xp pro in order to use xp pro for games and ubuntu for everything else. Yesterday, I was linked to an excellent article on how to do this, but then I realized that 40gb was probably not enough for what I wanted.

Today a friend handed me a wd2500me 250 gb external hard drive. He said that he had never formatted it, but had plugged it into his mac laptop, and that he was giving it away because it didn't work with what he had. 

I'm trying to figure out what to do here. Can I use the external drive for games? How do I format the drive so that it works with Ubuntu? Is there some way of keeping Ubuntu as is and downloading the xp to the external drive?

---

### Post by alexlafreniere on 2009-08-15
Since you want to use XP for games and those require faster disk performance than an external hard drive can provide, I would install both XP and Ubuntu to your internal drive. This will make your life a lot more pleasant since both OS's will be much speedier running off your internal hard drive than the external. Give XP about 25 GB and Ubuntu the remaining 15 GB. Then format the external drive as NTFS and use that for all your file storage. NTFS is readable by both Windows and Ubuntu so you will be able to share documents between the two OS's. Just be careful about junk files and unused programs piling up on the internal drive and you'll be good to go. A combined 290 GB of storage is more than enough for most people anyway (says the guy with a terabyte's worth of hard drives).

---

### Post by jalehtor on 2009-08-15
> **alexlafreniere said:**
> Since you want to use XP for games and those require faster disk performance than an external hard drive can provide, I would install both XP and Ubuntu to your internal drive. This will make your life a lot more pleasant since both OS's will be much speedier running off your internal hard drive than the external. Give XP about 25 GB and Ubuntu the remaining 15 GB. Then format the external drive as NTFS and use that for all your file storage. NTFS is readable by both Windows and Ubuntu so you will be able to share documents between the two OS's. Just be careful about junk files and unused programs piling up on the internal drive and you'll be good to go. A combined 290 GB of storage is more than enough for most people anyway (says the guy with a terabyte's worth of hard drives).

Thank you! Btw, Ubuntu's now using about 17 GB...I have my home files backed up on a disc. Should I remove those from Ubuntu before I partition? I don't know what I'm doing here.

---

### Post by sideaway on 2009-08-15
You can use Gparted to modify partitions, including resizing and moving. I suggest you use that, and you can set it up exactly how you like. I would backup all your data before you modify the partitions on your primary drive. I would use that to format the external as NTFS, then cut all your files (media/documents etc) to that external. This should free up space on your local disk.

I would then make a NTFS partition next to your ubuntu one and install XP on that.

Good luck!

---

