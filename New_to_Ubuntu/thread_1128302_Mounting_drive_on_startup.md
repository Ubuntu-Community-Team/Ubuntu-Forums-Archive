---
title: "Mounting drive on startup"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Tootler on 2009-04-17
I have most of my data on a FAT32 partition so that I can access it easily from both Ubuntu and Windows. 

I wish to mount the partition on startup I have done a search and found the relevant information [here:  https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab"). It all seems fairly straightforward - edit fstab to add the appropriate drive info. However there are two examples for mounting FAT partitions which have a different set of options. I would appreciate it if someone could explain these differences before I try it so I am clearer as to exactly what I need to include in fstab. 

The two examples are:

```
/dev/hda2 /media/data1 vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

/dev/sdb1 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0
```

All help appreciated.

Geoff

---

### Post by leonardo_neo on 2009-04-17
Before you do anything, let's first make the backup of your  fstab table. Run this command to back up your fstab.

> sudo cp /etc/fstab /etc/fstab_backup

Now you need not to worry about experiments. If something doesn't work, just replace your modified fstab with the backup one.

Now you can try both of these two option and try if that works with you. If any of these two works, then it is great.

For me, none of these two options work. I have a different set of line in my fstab to mount my FAT32 partition. There is a tutorial as well, try that too in case that one helps. Here is the link.....

[http://www.psychocats.net/ubuntu/mountwindowsfstab]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

Hope this helps :)

---

### Post by WorldTripping on 2009-04-17
You could also have a read of this:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by ravi_buz on 2009-04-17
A simple way is you type NTFS in add/remove and u will get one software just install it and it will mount the partition while start up no need to type anything

---

### Post by leonardo_neo on 2009-04-17
> **ravi_buz said:**
> A simple way is you type NTFS in add/remove and u will get one software just install it and it will mount the partition while start up no need to type anything

If you are talking about NTFS configuration tool, then it works only for NTFS partition, and not for FAT32.

---

### Post by stchman on 2009-04-17
> **Tootler said:**
> I have most of my data on a FAT32 partition so that I can access it easily from both Ubuntu and Windows. 

I wish to mount the partition on startup I have done a search and found the relevant information [here:  https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab"). It all seems fairly straightforward - edit fstab to add the appropriate drive info. However there are two examples for mounting FAT partitions which have a different set of options. I would appreciate it if someone could explain these differences before I try it so I am clearer as to exactly what I need to include in fstab. 

The two examples are:

```
/dev/hda2 /media/data1 vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

/dev/sdb1 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0
```

All help appreciated.

Geoff

This is all you need:

```

/dev/hda2  /media/data1 vfat  auto,defaults,rw  0   0
/dev/sdb2  /media/data2 vfat  auto,defaults,rw  0   0

```

If you want read only then substitute ro for rw.

Then do:
```
sudo mount -a
```

---

### Post by Tootler on 2009-04-18
Thanks for the suggestions. I will need to look at these and try things out. 

A Particular thanks for the reminder to backup fstab :oops:

Geoff

---

### Post by Tootler on 2009-04-22
Sorted. Thanks to this: [https://help.ubuntu.com/community/Au...ountPartitions](https://help.ubuntu.com/community/Au...ountPartitions)

Geoff

---

