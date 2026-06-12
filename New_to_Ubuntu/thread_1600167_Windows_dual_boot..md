---
title: "Windows dual boot."
date: 2010-10-18
forum: New to Ubuntu
---

### Post by Zombie Robot on 2010-10-18
I have it dual booted, But my windows got a virus and no I cant even long into windows. So How can I get rid of windows

---

### Post by coffeecat on 2010-10-18
Boot into Ubuntu, go to the Places menu and mount the Windows partition. Delete everything you can see (except the $RECYCLE.BIN and System Volume Information folders) and you have no Windows - just an empty NTFS partition. Which you can reformat if you want with Disk Utility in the System > Administration menu. Or Gparted in the live CD.

Or just reformat the Windows partition with Disk Utiity without deleting everything else first.

Once you've done either of those, open a terminal and...

```
sudo update-grub
```... to remove Windows from the grub menu.

Do you have a recovery partition or recovery DVDs or a Windows install disk?

---

### Post by Hippytaff on 2010-10-18
> **Zombie Robot said:**
> I have it dual booted, But my windows got a virus and no I cant even long into windows. So How can I get rid of windows

you can use gparted to get rid of it or just do a fresh install of ubuntu using the whole drive...back up important data first ;-)

---

### Post by Melon Bread on 2010-10-18
Is it a true dual boot, or did you use something like wubi?

---

### Post by Hippytaff on 2010-10-18
> **Melon Bread said:**
> Is it a true dual boot, or did you use something like wubi?
Good point

---

### Post by Zombie Robot on 2010-10-18
> **Hippytaff said:**
> you can use gparted to get rid of it or just do a fresh install of ubuntu using the whole drive...back up important data first ;-)
How can I just do a fresh install? Just put in the disk again? I dont have any data so nothing to back up lol

> **Melon Bread said:**
> Is it a true dual boot, or did you use something like wubi?
I think its true. Im not 100% tho.

---

### Post by Hippytaff on 2010-10-19
To do a fresh install just put the disk in and choose install once its booted, you will have two options, you can either let it do an automatic install, or you can choose to manually assign partitions - if you choose the second option have a look at this to get an idea of how you want to partition your disc - [http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)
 
There are other partitioning tutorials and advice on this forum...I would advise you to have a seperate /home partition :-)

---

