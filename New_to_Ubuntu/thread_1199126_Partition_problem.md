---
title: "Partition problem"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by StefanSeo on 2009-06-28
Guys this is my first post :lolflag:
I have a problem with partition. i formated the partition with gparted. Then when i mount my partition i have acces to it only to look what is inside. When i try to copy something on it, or even open, it gets me error. On my permissions tab it says that im not the owner & i cant change anything

---

### Post by LewRockwell on 2009-06-28
.

---

### Post by TeoBigusGeekus on 2009-06-28
Change the owner of the partition then
```
sudo chown yoursusername /media/wherever_the_drive_is_mounted
```

---

### Post by StefanSeo on 2009-06-28
Tnx, i changed the permissions.
However there is one folder lost+found, i still dont have permissons over that folder:mad:
ps it has 20 gigs memory, its empty but it says that it already has 1 gig used?

---

### Post by ahndoruuu on 2009-06-28
Umm...is there any particular reason you need authority over that particular folder?

If so, run 
```
gksudo nautilus
```

navigate to the folder. you will be able to do whatever you wish with it.

though i wouldn't recommend messing with permissions.

---

### Post by StefanSeo on 2009-06-28
> **ahndoruuu said:**
> Umm...is there any particular reason you need authority over that particular folder?

If so, run 
```
gksudo nautilus
```navigate to the folder. you will be able to do whatever you wish with it.

though i wouldn't recommend messing with permissions.
yeah, but it devouts me 1 gig space! Need to see whats inside :D
edit there is nothing inside and still 1 gig is used , btw thx guys it helped me alot

---

### Post by Captain_tux on 2009-06-28
> **LewRockwell said:**
> .

Helpful and informative...?

---

### Post by louieb on 2009-06-28
> **StefanSeo said:**
> there is one folder lost+found,

folder is created by program fsck (file system check) You can delete it but it will come back. Don't know why yours is so large. Mine is empty and around 16k in size.

---

### Post by egalvan on 2009-06-28
> **StefanSeo said:**
> there is one folder lost+found, :
ps it has 20 gigs memory, its empty but it says that it already has 1 gig used?

is it the PARTITION or the FOLDER that is using 1GB?

some Linux file systems reserve 5% for administrative chores,
so 1G out of 20G is right.

if it's the lost+found that is using 1GB, that's something else.

as other have stated 

```
gksudo nautilus
```

will start nautilus in "root" mode, allowing you to navigate, open, create and delete with abandon.

there are posts on how to empty these types of folders.

---

