---
title: "Installing on an existing partition..."
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Draclan12 on 2009-02-02
Well, right now I have 2 hard drives on my computer, one for OS and the other for storage.

My OS hard drive is partitioned into two, one for Windows XP and an empty one (had Vista on it, but I formatted it).

I want to install Ubuntu on the empty partition, so I popped in a disk and tried to get it working, but I had no luck.

I'm trying to get it to dual boot XP and Ubuntu, if you hadn't noticed..


I also have no experience with Linux.. ;)
Btw, using Ubuntu 8.10 desktop.

Thanks.

---

### Post by laffinet on 2009-02-02
> **Draclan12 said:**
> W

I want to install Ubuntu on the empty partition, so I popped in a disk and tried to get it working, but I had no luck.


Can you be a bit more specific. What did not work ? How far did you get ? What did you try ?

---

### Post by Draclan12 on 2009-02-02
> **laffinet said:**
> Can you be a bit more specific. What did not work ? How far did you get ? What did you try ?

Well, I just click Manual on the partition part and then choose my partition that's empty, when I click next it gives me an error..

I'll check in a bit and post the error.

---

### Post by bumanie on 2009-02-02
After choosing manual and checking the partition you wan to modify, you will have the choice of choosing either 'new' or 'edit' partition - then you can choose the size of the partition, what to filesystem to format it to and what to name it - eg choose edit, upper box choose size in mb's, next box choose filesystem type - ext3 ; bottom box name of partition such as / or /home. 
Advise to set up / formatted to ext3 of 8000mb (8gb), /home also formatted to ext3, large as you like and swap of 1-2gb. With swap you only have to choose the size and the filesystem type is named swap, there is no bottom window to fill in.

---

### Post by Draclan12 on 2009-02-02
> **bumanie said:**
> After choosing manual and checking the partition you wan to modify, you will have the choice of choosing either 'new' or 'edit' partition - then you can choose the size of the partition, what to filesystem to format it to and what to name it - eg choose edit, upper box choose size in mb's, next box choose filesystem type - ext3 ; bottom box name of partition such as / or /home. 
Advise to set up / formatted to ext3 of 8000mb (8gb), /home also formatted to ext3, large as you like and swap of 1-2gb. With swap you only have to choose the size and the filesystem type is named swap, there is no bottom window to fill in.

Can you explain what the home and swap is?

---

### Post by laffinet on 2009-02-02
/home is where all your documents, settings and applications will be stored. This should be your largest partition
/swap is used by applications and the OS if the RAM is full

Having a separate /home partitions will allow you to reinstall Ubuntu without loosing all your settings.

Did you find out what that error message was ?

---

### Post by Draclan12 on 2009-02-02
> **laffinet said:**
> /home is where all your documents, settings and applications will be stored. This should be your largest partition
/swap is used by applications and the OS if the RAM is full

Having a separate /home partitions will allow you to reinstall Ubuntu without loosing all your settings.

Did you find out what that error message was ?

Ahh, So does that mean that I have to have 2 partitions, one for /home and on for /swap?

And the error message, I will post once I get a chance..

---

### Post by laffinet on 2009-02-02
You have to have at least 2 partitions:

1 for root, which is where the OS is installed
1 for swap

/home can be included in the root partition, but for reasons explained above you might want to have a separate /home partition (would be my suggestion)

You don't need to create these partitions prior to starting the installation. It's done at the stage where you got the error message (via the manual/edit partitions option).

---

### Post by Draclan12 on 2009-02-02
> **laffinet said:**
> You have to have at least 2 partitions:

1 for root, which is where the OS is installed
1 for swap

/home can be included in the root partition, but for reasons explained above you might want to have a separate /home partition (would be my suggestion)

You don't need to create these partitions prior to starting the installation. It's done at the stage where you got the error message (via the manual/edit partitions option).

So should I just do the partitioning part thru the installer and not manually through windows?

---

### Post by laffinet on 2009-02-02
Yep. That's the way to go. That way you can edit/create partitions and assign mount points (as in "/" for root, /home for home and swap) at the same time.

So:

- start the installation
- down the track, pick manual partition
- edit partitions
- create one partition for root, choosing "/" for mount point (about 8 gig)
- one for swap, choosing swap for mount point (about 1-2 gig)
- one partition for home, choosing "/home" for mount point (as big as possible)

off you go

---

