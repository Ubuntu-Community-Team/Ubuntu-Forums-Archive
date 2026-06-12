---
title: "cp: Value too large for defined data type"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Mariane on 2009-07-16
Before partitioning a windows xp disk to install ubuntu I decided I wanted a full backup. 

Windows won't do a simple backup, it keeps saying "you don't have permission to do this", "you don't have permission to do that", etc. Even when I'm admin. Forget it. 

cp fails on a large .dll with error: "Value too large for defined data type". How can I overcome this? 

Mariane

---

### Post by LewRockwell on 2009-07-16
best advice: external hard drive equivilent or greater in size than your internal hard drive

then...use Clonezilla to create an identical clone to what you have now

I have never been disappointed with Clonezilla

.

---

### Post by OffAxis on 2009-07-16
Not the most elegant solution, but you can also use dd to make an exact copy of your drive.

```
dd if=inputFile of=outputFile
```

it'll make a bit by bit copy.

---

### Post by Elep.Repu on 2009-07-16
# rsync /dev/YOURDRIVE /media/BACKUPPLACE

Like maybe,


```
sudo mkdir /media/bak
sudo rsync /dev/sda2 /media/bak
```[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)
Try [Backintime]("http://backintime.le-web.org/")
[URL="http://backintime.le-web.org/"]
[/URL]

---

### Post by Mariane on 2009-07-16
Thank you. I tried rsync and it's doing something. 

I had to add a -r otherwise it just said "skipping directory ."

So it was:

rsync -rh /media/disk /media/backup_disk

The "h" is supposed to give me some indications of what it is doing but for the moment it is silent. 

Mariane

---

### Post by LewRockwell on 2009-07-16
> **Mariane said:**
> Thank you. I tried rsync and it's doing something. 

I had to add a -r otherwise it just said "skipping directory ."

So it was:

rsync -rh /media/disk /media/backup_disk

The "h" is supposed to give me some indications of what it is doing but for the moment it is silent. 

Mariane

assuming that was actually```
sudo rsync -rh /media/disk /media/backup_disk
```.

---

### Post by Mariane on 2009-07-16
Didn't work either, though it didn't fail on the same file. "Value too large for defined data type". 

Tried dd but it tells me "It's a directory". Is there a way to make it copy all the same? I don't really fancy doing this backup file by file... :/

Mariane

---

### Post by LewRockwell on 2009-07-16
> **Mariane said:**
> Didn't work either, though it didn't fail on the same file. "Value too large for defined data type". 

Tried dd but it tells me "It's a directory". Is there a way to make it copy all the same? I don't really fancy doing this backup file by file... :/

Mariane

what was your```
stuff here
```exactly?

---

### Post by Mariane on 2009-07-16
```

dd if=LFCMP13n.dll of=/<backup path>/LFCMP13n.dll

```

Answer was:
```

dd: reading `LFCMP13n.dll': Value too large for defined data type
512+0 records in
512+0 records out
262144 bytes (262 kB) copied, 0.0385191 s, 6.8 MB/s

```

---

### Post by Mariane on 2009-07-16
I took your advice LewRockwell (not about using code tags, though this also). I burned a cd with clonezilla and nearly erased all the stuff I have on the external hard drive with it. Will post about that, it might help someone. 

But this creates an image and I'm not sure it is the same thing as a copy of all the files in all the directories. Will see. If it is not the same I hope I can tell it to "restore" on another external hard disk to get my copy. 

I already knew I needed 2 computers, one to  look for troubleshooting help online when the other goes haywire. Now I apparently need 2 external hard disks as well. 

Mariane

---

