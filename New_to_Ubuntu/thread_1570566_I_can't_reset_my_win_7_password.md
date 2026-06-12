---
title: "I can't reset my win 7 password"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Snaze on 2010-09-08
I get this error:
 
Disks
 
Disk /dev/sda: 120gb
 
Canditade windows partitions found:
1: /dev/sda1 0,10gb
2: /dev/sda2 100 gb
3: /dev/sda3 10 gb
Mounting from /dev/sda2 with assumed filesystem type NTFS so, le's really check if it is NTFS?
 
NTFS signature missing.
Does not seem to be NTFS anyway, trying the Fat warriants instead
 
ERROR
Ntfs probe returned error code 12
sorry, cannot continue.
*Cancelled
 
Can somebody please help me with this problem?

---

### Post by endotherm on 2010-09-08
ok, what os are you on right now, and what app are you using?
if you are on ubuntu and you want to see if a disk is ntfs, please post back the output of 
```

sudo fdisk -l

```

---

### Post by DemonBob on 2010-09-08
I've great success with this tool. Download the iso, burn, boot to it, and follow the onscreen instructions.

[http://pogostick.net/~pnh/ntpasswd/](http://pogostick.net/~pnh/ntpasswd/)

---

### Post by endotherm on 2010-09-08
> **DemonBob said:**
> I've great success with this tool. Download the iso, burn, boot to it, and follow the onscreen instructions.

[http://pogostick.net/~pnh/ntpasswd/]("http://pogostick.net/%7Epnh/ntpasswd/")
+1. great tool.

---

### Post by Mark Phelps on 2010-09-08
The NTFS error you're getting doesn't indicate a permissions problem, it indicates a filesystem problem.

If you're trying to reset your Win7 password to login to Win7 and run CHKDSK to try and repair the filesystem, that just MIGHT work.

If you're mounting the Win7 OS filesystem read/write -- that is going to continue to give you problems like this.  You should NOT automount it (if you're doing that) and instead, only mount it through Places on an as-needed basis.

---

### Post by Snaze on 2010-09-09
Btw I'm running windows 7 64-bit that maybe the problem, 
I would be glad if you guys know other reset tools that can reset 64 bits

---

### Post by Mark Phelps on 2010-09-09
You could Google for Trinity Rescue Kit.  It's another of the Linux-based boot CDs that allows for password resets.  Don't know if it will work with 64-bit though.

---

### Post by Snaze on 2010-09-09
> **endotherm said:**
> ok, what os are you on right now, and what app are you using?
if you are on ubuntu and you want to see if a disk is ntfs, please post back the output of 
```

sudo fdisk -l

```
 
I am using 
[[COLOR=#444444]http://pogostick.net/~pnh/ntpasswd/[/COLOR]]("http://pogostick.net/~pnh/ntpasswd/")
and my OS is win 7 64 bit.

---

### Post by endotherm on 2010-09-09
> **Snaze said:**
> I am using 
[[COLOR=#444444]http://pogostick.net/~pnh/ntpasswd/[/COLOR]]("http://pogostick.net/%7Epnh/ntpasswd/")
and my OS is win 7 64 bit.
ok, my guess is that the offline editor is not ready for the latest version of ntfs, or that your filesystem is damaged. try the trinity disk mark suggested, and see if that helps. if not, you may want to try BartPE livecd and use it to do a check of your ntfs filesystems.

---

### Post by inkrypted on 2010-09-09
Ophcrack has done the job for me you can get it here [http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/). Although it does sound like a file system error I mean are you trying to mount it? If so and you get ntfs signature is missing it's not an ntfs drive. I would suggest you look at the output of sudo fdisk -l and make sure you are mounting the correct drive.

---

### Post by Snaze on 2010-09-09
I think my NTFS system is corrupted, so I think I will try to fix it with BartPE livecd, and yes I am sure I'm mounting on the right drive, I know Windows is into that drive. Any1 else got any other suggestions?

---

### Post by xjchen001 on 2012-01-21
Hi Snaze, 
How did you resolve your problem? Now I encounter the same error. When I check my system, I can see the file system is HPFS / NTFS.

---

### Post by lisati on 2012-01-21
Old thread. Probably *should* be moved.

---

