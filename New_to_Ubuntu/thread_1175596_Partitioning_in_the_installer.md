---
title: "Partitioning in the installer"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by zortec on 2009-06-01
I finally was able to get the installer going using the minimal CD.  But I am unsure how to partition at this point.  I created a 30GB partition in Windows that I want to break up and use 1-2GB for swap and the rest for root.  This is what it shows in the partition screen:  

SCSI1 - 320GB - ATA
#1 primary 104.9GB
#2 primary 31.5GB
pri/log 83.8GB

Do I want a manual or guided install? The guided install did 7.5GB for swap and 138 or such for root.  If I go with manual, I have to decide if the partition will be at the beginning or front of the drive and it has a lot of other choices that I am not sure about.

I hope that anyone will be able to offer some help.

---

### Post by Legace on 2009-06-01
I suggest you go with Manual.
Post a screenshot of the partitions so that I can explain what you need to do.

---

### Post by zortec on 2009-06-01
How can I post a screenshot?  I have to boot into Windows since Ubuntu is not yet installed.

---

### Post by Legace on 2009-06-01
> **zortec said:**
> How can I post a screenshot?  I have to boot into Windows since Ubuntu is not yet installed.

Don't you have a Ubuntu Live CD?
Boot into that and post a screenshot ;)

---

### Post by zortec on 2009-06-01
> Don't you have a Ubuntu Live CD?
Boot into that and post a screenshot 

I could not get the Live CD to work so I used the Minimal CD as an alternative to run the installer.   That is why it would be hard to post a screenshot. :)

---

### Post by Legace on 2009-06-01
> **zortec said:**
> I could not get the Live CD to work so I used the Minimal CD as an alternative to run the installer.   That is why it would be hard to post a screenshot. :)

Oh, so you have to create partitions through Terminal? Then I can't help ya, sorry :/
Try posting in [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)
You'll have a better chance of getting an answer ;)

---

### Post by LewRockwell on 2009-06-01
> **zortec said:**
> I finally was able to get the installer going using the minimal CD.  But I am unsure how to partition at this point.  I created a 30GB partition in Windows that I want to break up and use 1-2GB for swap and the rest for root.  This is what it shows in the partition screen:  

SCSI1 - 320GB - ATA
#1 primary 104.9GB
#2 primary 31.5GB
pri/log 83.8GB

Do I want a manual or guided install? The guided install did 7.5GB for swap and 138 or such for root.  If I go with manual, I have to decide if the partition will be at the beginning or front of the drive and it has a lot of other choices that I am not sure about.

I hope that anyone will be able to offer some help.

 Looks like you'll have to go with the manual since the guided is allocating too much for swap.

---

