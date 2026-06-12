---
title: "Backup entire partition how"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by EgoGratis on 2010-06-25
I have quite a lot partitions on my HDD. And some times i try new things and quite easily my HDD partitions look like this:

[B]XP
Ubuntu
Kubuntu
Fedora
Mandriva
FreeBSD
...[/B]

A do a full XP partition backup with Acronis True Image. And i like it. If i do something wrong. It takes me about 10 minutes to restore everything.

How about Ubuntu. What should i do. I think clean install + all updates every time is an option. But i would like to learn something more advanced.

I was experimenting with **rsync**. But i don't know if it is appropriate for backing up and restoring entire partition. I have achieved good results with home folder.

So bottom line. What do you recommend. I install (K)Ubuntu and i use it a while. Then i experiment a lot. It gets broken by me. **I would like to restore it in 10 minutes.**

---

### Post by mk1w86 on 2010-06-25
If you want to take images of your drive or partitions take a look at Clonezilla:

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by howefield on 2010-06-25
> **EgoGratis said:**
> backup with Acronis True Image. And i like it.[/B]

An Acronis start up disk would work with Linux partitions, although last time I checked, it didn't support ext4 except for sector by sector, meaning backups were pretty huge, but that may have changed since then.

You might take a look at Clonezilla, which has a similar function to Acronis.

clonezilla.org

---

### Post by warfacegod on 2010-06-25
Remastersys might be useful also.

---

### Post by EgoGratis on 2010-06-25
So basically if i understand correctly. If i download Clonezilla Live CD. I can make backup of entire disk or single partition with practically any (supported) OS (file system) on it. And i can use it for XP, Ubuntu, Kubuntu. Mandriva, FreeBSD operation systems and their file systems...

And i can restore that backup as long restore partition is the same size or larger of the original. It evan backups Grub and Grub2.

On Clonezilla home page i see that only used blocks are used for practically all the mayor file systems and OS. And not sector by sector backup/restore. So size of the backup isn't large.

Hm. This sounds really good. Are there any draw backs. Compared to Acronis True Image Live CD for example? If you (the users) can confirm my data is safe with Clonezilla i will use it. By safe: Does Clonezilla have proven history and if it has proven it self as a good stable and safe software for home and maybe even professional usage.

---

### Post by nishant.thomas on 2010-06-25
I think Clonezilla can also make image of unsupported filesystems sector-by-sector, but it will result in huge image size.

---

### Post by mk1w86 on 2010-06-25
> **EgoGratis said:**
> So basically if i understand correctly. If i download Clonezilla Live CD. I can make backup of entire disk or single partition with practically any (supported) OS (file system) on it. And i can use it for XP, Ubuntu, Kubuntu. Mandriva, FreeBSD operation systems and their file systems...

And i can restore that backup as long restore partition is the same size or larger of the original. It evan backups Grub and Grub2.

On Clonezilla home page i see that only used blocks are used for practically all the mayor file systems and OS. And not sector by sector backup/restore. So size of the backup isn't large.

Hm. This sounds really good. Are there any draw backs. Compared to Acronis True Image Live CD for example? If you (the users) can confirm my data is safe with Clonezilla i will use it. By safe: Does Clonezilla have proven history and if it has proven it self as a good stable and safe software for home and maybe even professional usage.

Yes, I would definitely say so and I'm sure others would agree that it is as good, if not better than many commercial solutions. ;)

You are pretty much correct in your description and if you take an image of an entire disk it backs up the MBR as well (which Grub is usually installed to).  I haven't used Acronis True image myself so I can't really give any comparison.

---

### Post by EgoGratis on 2010-06-25
Thanks for all your answers. You helped me a lot. I have enough valuable information now. I will use Clonezilla Live CD. And i am downloading:


**Stable (Debian-based) - clonezilla-live-1.2.5-17-i686.iso**


I will mark this thread as solved. 

Thanks again for your help and support!

---

### Post by SoFl W on 2010-06-25
> **howefield said:**
> An Acronis start up disk would work with Linux partitions, although last time I checked, it didn't support ext4 except for sector by sector, meaning backups were pretty huge, but that may have changed since then. 

I know when I was dual booting with OpenSuse/W2K, Acronis 9 would back up the entire drive, didn't care if it was Linux or not.  (I believe Acronis boot disk is Linux based)  However when I installed Ubuntu it wouldn't see the Linux partitions.  Perhaps it is because they are ext4.  Thank you for that insight, I will have to give Clonezilla a try.

---

