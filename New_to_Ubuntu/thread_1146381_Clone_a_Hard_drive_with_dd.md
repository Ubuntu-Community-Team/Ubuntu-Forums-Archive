---
title: "Clone a Hard drive with dd"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2009-05-02
Hi
I want to clone a hard drive to a bigger one.
The source has Ubuntu on it.
I want to use dd command to clode disk, but need to
know how to determine the device (sda, sdb sdc) to
create my dd command.  How do I do that ?

Don't want to delete data.

Thanks.

---

### Post by llamabr on 2009-05-02
The output of 

```
cat /etc/fstab
```
or
```
df
```

will tell you which drives are currently mounted, along with their mount points.

---

### Post by Paqman on 2009-05-02
> **Pierrot Lafouine said:**
> 
I want to use dd command to clode disk, but need to


Not a very good idea. DD will copy every single bit on the drive, including all the blank space. SO unless your drive is totally full it's a really inefficient way to do it.

I'd recommend [partimage]("apt:partimage") instead. It's also available on the [System Rescue CD]("http://www.sysresccd.org/") and on the [Clonezilla LiveCD]("http://clonezilla.org/").

---

### Post by Pierrot Lafouine on 2009-05-04
Thank you all.
Clonezilla worked fine, even with these 1000 questions I didn't know what to answer.

Still some questions :
1) It detected one drive as SDA and other drive as HDA, why not SDA and SDB
or HDA and HDB ?
2) I tried GOST and didn't work.  It looks to me it didn't copy the swap
partition. Why GOST didn't worked ?  Is it because its a Windows base
programed ? :lolflag:

---

### Post by SnappyU on 2009-12-19
Drives on IDE appear as HDA, HDB etc while drives on USB (external) or SATA appear as SDA, SDB etc 

USB Thumb drives also appear as such.  Some of the built-in memory 
 card readers sit connect internally via USB, so the cards appear as SDA, SDB as well.

:)

> **Pierrot Lafouine said:**
> Thank you all.
Clonezilla worked fine, even with these 1000 questions I didn't know what to answer.

Still some questions :
1) It detected one drive as SDA and other drive as HDA, why not SDA and SDB
or HDA and HDB ?
2) I tried GOST and didn't work.  It looks to me it didn't copy the swap
partition. Why GOST didn't worked ?  Is it because its a Windows base
programed ? :lolflag:

---

