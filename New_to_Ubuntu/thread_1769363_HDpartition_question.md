---
title: "HD/partition question"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by bneva on 2011-05-27
On all other version of Ubuntu I have had a list of my other partitions (like my windows) I believe under the "Places" tab but now it is gone.  I know how to manually mount the drive but I am curious as to why they do not show up any more.  It made it much easier!

Thanks

---

### Post by wildmanne39 on 2011-05-28
> **bneva said:**
> On all other version of Ubuntu I have had a list of my other partitions (like my windows) I believe under the "Places" tab but now it is gone.  I know how to manually mount the drive but I am curious as to why they do not show up any more.  It made it much easier!

ThanksHi, if you are using natty open file manager and it should show windows drive on the left of the window.

---

### Post by bneva on 2011-06-23
> **wildmanne39 said:**
> Hi, if you are using natty open file manager and it should show windows drive on the left of the window.

The only drives it shows is the one I am using, I can't click my windows partition like I used to be able to.  I have to manually mount everything.  Before I could just click the partition, type in password and there it was on my desktop.

---

### Post by wildmanne39 on 2011-06-23
> **bneva said:**
> The only drives it shows is the one I am using, I can't click my windows partition like I used to be able to.  I have to manually mount everything.  Before I could just click the partition, type in password and there it was on my desktop.Hi, for some reason they are not auto mounting, my do. Open disk utility and mount them,  and see if that fixes your problem, if not you will have to edit your fstab.

---

### Post by Mr Stoozer on 2011-06-23
Doesn't it depend on whether they're/were mounted in /mnt or /media, as to whether they show in Nautilus' Places?

---

### Post by wildmanne39 on 2011-06-24
> **Mr Stoozer said:**
> Doesn't it depend on whether they're/were mounted in /mnt or /media, as to whether they show in Nautilus' Places?Hi, all of mine in the file manager including windows partitions show /media, but on the hard drive it shows /dev/sda. I am not an expert at fstab so I am going to leave the how to edit it up to someone else.

---

### Post by bneva on 2011-06-29
The disk utility doesn't even open for me.

---

### Post by amjjawad on 2011-06-30
Not a solution but just to make sure everything is ok.

From Terminal, please run:

```
sudo fdisk -l
```That's small "L".

Please copy and paste the output here between "CODE" tags or select the output and click "#".

---

