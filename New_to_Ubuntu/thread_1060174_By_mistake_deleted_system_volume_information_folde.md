---
title: "By mistake deleted system volume information folder"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Ant01 on 2009-02-04
Can someone please help, I was trying to free up some space for backups on a NTFS partion and I deleted the system information folder. I think I messed up as I can't mount the directory now. 

What can I do? I also tried booting from a Linux disc to recreate the partition but it seems that the disc is corrupt. Is there another way I can recreate the partition or restore the system folder?:(

---

### Post by vikramaditya on 2009-02-04
see if dis do be helpin' ya . . . ;)

[http://ubuntu-recover-ntfs.qarchive.org/](http://ubuntu-recover-ntfs.qarchive.org/)

**EDIT**  ugh...belay that, matey!  The rum's not free!

---

### Post by Ant01 on 2009-02-04
Thanks for that but I don't have any important info on the partion so I don't need to purchase a recovery tool, I just want to use the partition again and don't have a disk to recreate the partition:popcorn:

---

### Post by mister_pink on 2009-02-04
I'm fairly sure that folder isn't important, I always delete it, its just stuff windows creates. If you're using ntfs I assume you have a dual boot, in which case you could use the disk checking tools there.

Otherwise theres this advice from [this]("http://http://ubuntuforums.org/showthread.php?t=900543") thread.

> **drs305 said:**
> The best option is to remount in Windows and then shut down cleanly. You can force mount it in linux. The other option is to install and run the following to clear the error messages:
```
sudo aptitude install ntfsprogs
ntfsfix /dev/*partition.name*

```

It resets the journal but will not actually repair any 'damage' to the disk. It should clear the error and allow a normal mount. You may need to use 'sudo' with the ntfsfix command...

---

### Post by Ant01 on 2009-02-04
My dual boot on windows isn't woking anymore, I am using the computer as a server only booting with linux. I ran the command ntfsfix /dev/partition.name and it seems to work but when I mount the partition it is not visible:(

> **mister_pink said:**
> I'm fairly sure that folder isn't important, I always delete it, its just stuff windows creates. If you're using ntfs I assume you have a dual boot, in which case you could use the disk checking tools there.

Otherwise theres this advice from [this]("http://http://ubuntuforums.org/showthread.php?t=900543") thread.

---

### Post by mister_pink on 2009-02-05
What is the mount command you're using?

---

### Post by Ant01 on 2009-02-05
> **mister_pink said:**
> What is the mount command you're using?

sudo mount /dev/sdb1 /media/sdb1

---

### Post by brainac0cult on 2009-02-05
no!!!! dont do that!!!

---

### Post by Ant01 on 2009-02-05
> **brainac0cult said:**
> no!!!! dont do that!!!

Don't do what? :confused:

---

