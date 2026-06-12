---
title: "300GB Harddisk, 27GB used....but ZERO available"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by mistypotato on 2010-10-17
Hmmmmmmmm....

odd problem today.

My 300GB Hard Disk is reporting "Full" yet the total of all files used on the disk is only 27GB

The only two things left I can think of are.....

1). Corrupt file system (passed fsck with no errors)
2). HUGE hidden file(s) somewhere (or lots of hidden files).

Could they be in Lost and Found?  (that's about the only place I haven't checked).

Anyone else have this problem?

---

### Post by Verbeck on 2010-10-17
Have you tried using the disk usage analyser in accessories?

---

### Post by luvshines on 2010-10-17
Also check ~/.local/share/Trash and same in / too

---

### Post by amjjawad on 2010-10-17
> **mistypotato said:**
> Hmmmmmmmm....

odd problem today.

My 300GB Hard Disk is reporting "Full" yet the total of all files used on the disk is only 27GB

The only two things left I can think of are.....

1). Corrupt file system (passed fsck with no errors)
2). HUGE hidden file(s) somewhere (or lots of hidden files).

Could they be in Lost and Found?  (that's about the only place I haven't checked).

Anyone else have this problem?

Hidden files? I don't think so at all.
Are you Dual Booting with another OS?

Could you access GParted (System > Administration > GParted), take a screen shot and attach it.

---

### Post by mistypotato on 2010-10-17
> **Verbeck said:**
> Have you tried using the disk usage analyser in accessories?

Hello,

Yes.  Nothing peculiar there.

---

### Post by mistypotato on 2010-10-17
> **amjjawad said:**
> Hidden files? I don't think so at all.
Are you Dual Booting with another OS?

Could you access GParted (System > Administration > GParted), take a screen shot and attach it.

No,
Not dual booting.
Unmounted any and all media.
Gparted shows sda2 298GB - 278GB Used on Sda5  -  2GB swap file

The 278GB used would explain the disk full problem....

But that6's where the mystery begins...

I can only find 27GB used on the drive :confused:

I individually went through each and every folder from root on down and also checked the size of each directory.   It just doesn't add up.

It's as though there's about 260-270GB of mystery files.

Lost and Found is the only place I haven't looked because it's protected / hidden.
Perhaps I should chown it and look in there?

---

### Post by fbobraga on 2010-10-17
hm... smells like non partitioned space - use **gparted**

Edit: after your post, mine don't makes sense - try to find big files in your disk with ```
find / -type f -size +500M -ls
```(use ***sudo*** to avoid "permission denied" problems)

---

### Post by JackNocturne on 2010-10-17
i had the same problem, i solved it by booting from live CD and using **Gparted** to **check** my **filesystem**. I never understood why it showed that way. Hope it works from you.

---

### Post by mistypotato on 2010-10-17
> **JackNocturne said:**
> i had the same problem, i solved it by booting from live CD and using **Gparted** to **check** my **filesystem**. I never understood why it showed that way. Hope it works from you.

I'm online and working from a LiveCd right now  :)

STILL can't find anything tho  :confused:

---

### Post by JackNocturne on 2010-10-17
When you fix the filesystem does it report **no errors**? Also do you use Gparted or Disk utility or command line?

---

### Post by amjjawad on 2010-10-17
> **mistypotato said:**
> No,
Not dual booting.
Unmounted any and all media.
Gparted shows sda2 298GB - 278GB Used on Sda5  -  2GB swap file

The 278GB used would explain the disk full problem....

But that6's where the mystery begins...

I can only find 27GB used on the drive :confused:

I individually went through each and every folder from root on down and also checked the size of each directory.   It just doesn't add up.

It's as though there's about 260-270GB of mystery files.

Lost and Found is the only place I haven't looked because it's protected / hidden.
Perhaps I should chown it and look in there?

Just curious. Why do you have ext2 and ext3? what version of Ubuntu do you have?

I think there's something wrong with your filesystem. I still don't think it's hidden files. What kind of hidden files with more than 200GB of size? I don't really think so.

If you're not dual booting and you don't mind to wipe your HDD and start again, I'd suggest to remove everything and re-partition your HDD.
If you're using Ubuntu 10.04 or 10.10, the filesystem format should be ext4.

---

### Post by mistypotato on 2010-10-17
Well, my guess that it was large hidden files was right.

Hidden files.

A while back I had inadvertently set up a backup scheme and forgot about it.

Odd thing is I never remember the computer being sluggish as would be expected during a backup so that part still baffles me as to how the files were created without me being aware of it. :confused:

About 230 GB worth of backups going back to last year was hiding in a protected hidden backup directory.

Thanks for all the replies !!!!!!!!!!!

:KS:KS:KS:KS:KS

---

### Post by JackNocturne on 2010-10-17
Cheers, glad you found your data.

---

### Post by amjjawad on 2010-10-17
> **mistypotato said:**
> Well, my guess that it was large hidden files was right.

Hidden files.

A while back I had inadvertently set up a backup scheme and forgot about it.

Odd thing is I never remember the computer being sluggish as would be expected during a backup so that part still baffles me as to how the files were created without me being aware of it. :confused:

About 230 GB worth of backups going back to last year was hiding in a protected hidden backup directory.

Thanks for all the replies !!!!!!!!!!!

:KS:KS:KS:KS:KS

If these are BACKUP files so yes. I thought you're talking about System Files and stuff.

Anyway, in my opinion, the best place to save a backup files is the external HDD. That would give you more freedom and more options. You could then play around with partitions, etc.

---

### Post by mistypotato on 2010-10-18
> **JackNocturne said:**
> Cheers, glad you found your data.

Thanks for your help :P :KS

---

### Post by mistypotato on 2010-10-18
> **amjjawad said:**
> If these are BACKUP files so yes. I thought you're talking about System Files and stuff.

Anyway, in my opinion, the best place to save a backup files is the external HDD. That would give you more freedom and more options. You could then play around with partitions, etc.

No problem.

I "vaguely" remember messing around with "simple Backup" a LONG time ago so I guess I accidentally left it running....**[COLOR="Red"]but what's really odd is that it made these gigantic (11GB) backup files and I never recall there being ANY sluggishness in the PC at all[/COLOR]** :confused:

UNLESS >>> it ONLY did them on those rare nights I left the computer running overnight ???  (the timestamps dont agree with that)

I'm having trouble believing how it could have made those huge files without me being aware that a LOT of resources were being used.

---

