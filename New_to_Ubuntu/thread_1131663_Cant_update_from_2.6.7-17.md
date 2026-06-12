---
title: "Cant update from 2.6.7-17"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Nudzacysie on 2009-04-21
Well im not really new to computers but i am to ubuntu and i cant seem to update from 2.6.7-17 i dont know why it doesnt but the hard drive has space and i cant think of no other reason why this is happening.

---

### Post by Walter Melon on 2009-04-21
> **Nudzacysie said:**
> Well im not really new to computers but i am to ubuntu and i cant seem to update from 2.6.7-17 i dont know why it doesnt but the hard drive has space and i cant think of no other reason why this is happening.

what can't you update and can you show any errors that pop up?

---

### Post by skymera on 2009-04-21
What Ubuntu version are you running?

2.6.7 is really old.
Perhaps your Ubuntu has been dropped from updates.

---

### Post by Nudzacysie on 2009-04-21
It said something about /boot and i just downloaded it from the ubuntu site but i defenetly know it has something to do with backing up because it starts up normal then halfway during the little status line it says something bout /boot cant make backup or something like that.

---

### Post by nandemonai on 2009-04-21
We really need more information to be able to assist you.

Start with the output from these commands in terminal:

```
cat /etc/lsb-release
```

```
df -h
```

How are you trying to update and what errors are you receiving? Be specific please.

---

### Post by Nudzacysie on 2009-04-21
Well the little star with the arrow poiniting downwards is what it says that it needs to download new update basicly the "update manager" and then after i press install it tells me this:

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

 Now i cant even hear anything and then i cant copy what the terminal says.

---

### Post by nandemonai on 2009-04-22
Is this a wubi install on a fat32 file system?

I came across these two bugs that may be related...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339500](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339500)

[https://bugs.launchpad.net/wubi/+bug/252900](https://bugs.launchpad.net/wubi/+bug/252900)

---

### Post by Nudzacysie on 2009-04-22
So basicly i have to uninstall and then reinstall the whole thing?

---

### Post by nandemonai on 2009-04-23
> **Nudzacysie said:**
> So basicly i have to uninstall and then reinstall the whole thing?

You didn't answer my question.

If this is indeed a wubi install on a fat32 partition then one option would be to convert the fat32 file system to ntfs but before considering that I'd highly recommend a complete backup.

Note: You can only convert from fat32 to ntfs if the file system you're trying to convert is not the active system drive. ie not where windows is loading from. Usually c:\. Unless you use some form of live cd to do it.

---

### Post by Nudzacysie on 2009-04-23
Im running unbuntu from a external hard drive and windows from the C:/ Drive and yes it is a wubi installation on a fat32 the reason why i didn't respond at first was because i didnt know sorry about that. =P

---

### Post by nandemonai on 2009-04-23
> **Nudzacysie said:**
> Im running unbuntu from a external hard drive and windows from the C:/ Drive and yes it is a wubi installation on a fat32 the reason why i didn't respond at first was because i didnt know sorry about that. =P

No worries ;)

From what I was reading in those bug reports, converting the disk to ntfs should solve your issues then.

Since this isn't your system disk then you _shouldn't_ have any problems.

I'd still recommend a backup of said drive before converting though.

[http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

Good luck.

---

### Post by Nudzacysie on 2009-04-24
Wow you i should of had listened to you right now it sucks because i have to re install due to the fact that i didn't back up.

---

