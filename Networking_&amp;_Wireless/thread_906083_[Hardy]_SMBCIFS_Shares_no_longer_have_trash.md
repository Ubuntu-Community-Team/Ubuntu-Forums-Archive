---
title: "[Hardy] SMB/CIFS Shares no longer have trash?"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by callan79 on 2008-08-31
Hi All,

I've been using Ubuntu since 2006, often having samba shares mounted on my computer, for example the shared music and photo storage in our house. These shares used to be mounted with smbfs, now are mounted with cifs.

In the past (feisty, etc), any files I deleted from a mounted share would be moved to folder called "trash.username" on that share, and I could see it in my trash.

This has always been one of my selling points over Windows, which has always just permanently deleted files removed from shares.

But with hardy, this no longer happens - the files are deleted permanently.

I'm using the same mount commands in fstab as I always have been :

```
//192.168.7.1/media /media/media cifs auto,user=me,pass=mine,setuids
```

Anyone know why this has changed? Anyone know how to make the trash work again?

I can only think something has changed in hardy, since the system location of trash has changed too.

Any thoughts appreciated.

Cheers
Callan

---

### Post by callan79 on 2008-08-31
As a side request ... can anyone tell me if they have the same issue?

I mean, if you use Ubuntu, and you mount another Ubuntu or Windows machine's share, what happens when you delete a file? Does it go to trash somewhere, or deleted permanently?

Thanks
Callan

---

### Post by Dagg on 2008-09-30
Yes, I have the same issue,and it's very annoying.

Have you found a solution ?

---

### Post by cariboo on 2008-10-01
I still use smbfs to mount my shares, and I'm glad thers arn't any extra trash directories cluttering up things. I get so annoyed when I delete a file and then have to go to a trash directory to delete it again. I don't delete files in directories that hold important information, the directories are backuped up at least three times, I have Business data and email backups going back to 1995 when I first got internet access, can you say the same thing? With the price of hard drives these days there is no reason not to have enough external drive to backup your data at least twice.

Sorry for the rant, but the trash can is one innovation that MS and Gnome/KDE should never have copied from Apple. It doesn't make people responsible for thier actions.

Jim

---

### Post by callan79 on 2008-10-02
> **cariboo907 said:**
> Sorry for the rant, but the trash can is one innovation that MS and Gnome/KDE should never have copied from Apple. It doesn't make people responsible for thier actions.


Hi All,

I haven't found a solution yet - I figured it's not worth stuffing around since 8.10 is coming soon, I'll troubleshoot it then.

Jim, I completely agree that people should learn to be responsible for their actions. Personally, I do backups regularly (perhaps not as often as I should), but I can't say the same thing for the 11 people that I've converted to Ubuntu in the last 18 months.

I guess my post wasn't so much a cry for a trash can, but more of a "hey, why has this suddenly stopped working?"

Cheers :-)
CD

---

### Post by callan79 on 2008-10-06
> **callan79 said:**
> In the past (feisty, etc), any files I deleted from a mounted share would be moved to folder called "trash.username" on that share, and I could see it in my trash.

But with hardy, this no longer happens - the files are deleted permanently.

```
//192.168.7.1/media /media/media cifs auto,user=me,pass=mine,setuids
```



Hi All,

I may have just solved this puzzle. Hoping someone else can try and let me know their result!

I've just installed Intrepid, and I thought it was about time that I reviewed my FSTAB configuration.

My old FSTAB line (per quote above) used to have 'setuids' in the options. I changed my FSTAB to look like this:

```
//192.168.7.1/shared /media/shared cifs noauto,user=me,password=mine,uid=callan,gid=callan 0 0
```

Happy to say that items deleted from this share now go to the trash! The files physically exist in /media/shared/Trash.1000/ which is on the mounted drive itself.

Just to test, I changed it back to 'setuids' and confirmed, trash no longer worked.

Cheers
Callan

---

