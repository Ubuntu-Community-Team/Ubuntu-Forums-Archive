---
title: "How do I format my computer entirely."
date: 2010-12-13
forum: New to Ubuntu
---

### Post by QuentinK on 2010-12-13
I was wondering how I would go about wiping my harddrive completely clean, so I can install my Windows XP again, so I can try to dualboot linux again.
I have disks to install XP and all my drivers and such, I just need to know how to basically set my HDD back to its factory settings.

Any help is welcomed and appreciated <3


~Quentin

---

### Post by uRock on 2010-12-13
Use a Ubuntu LiveCD. Boot into the live session and go to System> Administration> Gparted or Partition Editor, whichever one is there, then you can delete the current partitions, create the NTFS for Windows then leave the rest blank until you go to install Ubuntu/Linux.

---

### Post by amjjawad on 2010-12-13
> **uRock said:**
> Use a Ubuntu LiveCD. Boot into the live session and go to System> Administration> Gparted or Partition Editor, whichever one is there, then you can delete the current partitions, create the NTFS for Windows then leave the rest blank until you go to install Ubuntu/Linux.

+1

And please, make sure to create 1 Primary Partition for Windows and create an Extended Partition with whatever remaining space you got. For example, if your HDD is 250GB then:

50GB is Primary Partition for Windows
200GB is Extended Partition

Inside the Extended Partition, you'll be able to create many Logical Partition.

Perhaps you'll not understand that at the moment but later on, you'll need it ;)

On my signature, you'll find a facebook page. In that page, there is a guide for GParted (pictures) and these pictures will be very helpful to you.

Also, check this:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by QuentinK on 2010-12-14
Thanks all for the reply, I'll use the LiveCD on my flash drive that I used to accidentally install Ubuntu in the first place :P.
But I may have to make a tiny partition for Ubuntu next time since my HDD is only 80gb, so I don't have very much space.
But again thanks for all the help.

---

### Post by uRock on 2010-12-14
If you don't plan to save any data to it, then Ubuntu will play happily with five or six GB of space. If you need to save data, then you can save it into the NTFS partition, where you'll be able to access it with both Windows and Ubuntu.

---

### Post by QuentinK on 2010-12-14
Why that sounds just lovely.
When I get my XP up and kicking in the next 45 minutes or so I'll do that.

---

### Post by amjjawad on 2010-12-15
One advice that won't harm and will keep you in the safe side.
Do NOT share your C: drive (where Windows is Installed) with Ubuntu. Try to create a separate partition for that. 

Good luck!

---

