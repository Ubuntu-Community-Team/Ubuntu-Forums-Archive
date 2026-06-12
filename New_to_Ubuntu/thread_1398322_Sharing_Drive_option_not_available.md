---
title: "Sharing Drive option not available"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by pbateman on 2010-02-04
Hi Guys,
Quick question, I have an external harddrive which I use to backup data . Currently I am backing things form the Desktop it is physically attached to only. This is working great.
I would like to, however, share this drive so i can also backup data from my laptop.
The thing is i am able to share folders from my desktop PC, but when I try to share a drive (eg. the external drive) itself, I don't get a sharing option.
Is it possible to share this drive as a whole or do I have to share folders within it but not the entire drive itself?
I do not have any windows PC's, both laptop and desktop have Ubuntu 9.10
I thought about installing Samba but from what I understand this is so that you can create shares that can be accessed/visible by Windows machines. Since both my machines have Ubuntu is there a native way of sharing this?
Thanks!!

---

### Post by thatguruguy on 2010-02-04
I use samba to share files between my desktop and my laptop, both of which use ubuntu. It seems to be the easiest way.

---

### Post by Monotoko on 2010-02-04
Use this:

```
sudo nautilus /media
```

then find the mounted drive you would like to share (it will only appear in /media while its plugged in)

---

### Post by thatguruguy on 2010-02-04
> **Monotoko said:**
> Use this:

```
sudo nautilus /media
```then find the mounted drive you would like to share (it will only appear in /media while its plugged in)

Why does he have to use sudo to do that?

---

### Post by Morbius1 on 2010-02-04
What is this external drive formatted in - ext3 / fat32 / ntfs ?

Who owns the mount point - root / you ?

Do an [B]ls -dl /path-to-mount-point
[/B]So we can see who owns it and what permissions it has

---

### Post by mk1w86 on 2010-02-04
> I thought about installing Samba but from what I understand this is so that you can create shares that can be accessed/visible by Windows machines. Since both my machines have Ubuntu is there a native way of sharing this?


The sharing option in Ubuntu uses Samba as far as I am aware. :-k

If however you only have Linux machines I would recommend NFS over Samba. ;)  

There is a guide on setting up NFS here:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Here is a more simple NFS setup guide: :D

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by Morbius1 on 2010-02-04
> The thing is i am able to share folders from my desktop PC

I forgot to ask something else, sorry. There are two ( Samba ) methods of sharing in Ubuntu so I want to see how you're sharing them:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

---

### Post by pbateman on 2010-02-04
Thanks for the tips guys, Im at work now but will try them once i get back home tonight.
As far as how Im sharing folders, from what I recall,just like in Windows, right clicking and sharing from the menu. Of course  though when I do this on the drive itself, there's no sharing option. ..
Thanks again for the info....I'll give a few of these a shot tonite

---

### Post by pbateman on 2010-02-04
> **Monotoko said:**
> Use this:

```
sudo nautilus /media
```

then find the mounted drive you would like to share (it will only appear in /media while its plugged in)

Thanks tried this first and worked, gave me the option of sharing it whereas before i did not have it.
I am intrigued by NFS but looks pretty complicated...i'll look into it as well though just for knowledge purposes at least. Would this be considered a Samba share then? not NFS?
Thanks all!

---

