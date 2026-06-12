---
title: "Format a drive with ubuntu on it"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by herbertg on 2009-11-06
Have another machine that has Ubuntu on it. I can't format the drive with an Xp disc. It says it has a my harddrive might have a virus. How do I format it to install XP.

Thanks

---

### Post by SlugSlug on 2009-11-06
delete the partition within xp install

---

### Post by tarps87 on 2009-11-06
Boot using the Ubuntu live cd/USB, open up gparted (partition editor), it should be under system -> admin.
Now select the correct hard drive, delete all partitions, create a new full sized part ion and format it as fat32.

**NOTE: THIS WILL REMOVE ALL THE DATA ON THE HARD DRIVE, PLEASE MAKE SURE YOU BACK UP ANY DATA YOU WANT FIRST!**

---

### Post by MelDJ on 2009-11-06
> **tarps87 said:**
> boot using the ubuntu live cd/usb, open up gparted (partition editor), it should be under system -> admin.
Now select the correct hard drive, delete all partitions, create a new full sized part ion and format it as fat32.

**note: This will remove all the data on the hard drive, please make sure you back up any data you want first!**

+1

---

