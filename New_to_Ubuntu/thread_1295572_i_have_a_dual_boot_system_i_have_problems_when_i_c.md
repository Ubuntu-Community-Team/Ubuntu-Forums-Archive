---
title: "i have a dual boot system i have problems when i copy"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by jimbean on 2009-10-19
i have ubuntu 9.04 and vista premium on same harddisk
when i copy files and folders from the linux partition
to the vista partition 
they automatically get shared in the vista partition
meaning they have the shared attribute turned on by default by vista
is this a bug and or is there a step i am missing 
I dont want the files to be shared in the vista partition
i know that if i right click the file or folder and choose,to not share
in vista it will undo sharing 
but vista takes a long time to complete the process
any help would be nice

---

### Post by martrn on 2009-10-19
> **jimbean said:**
>  [..] when i copy files and folders from the linux partition to the vista partition they automatically get **shared** in the vista partition [..] meaning [..] **shared** [??] turned on by default by vista [..] I don't want the files to be **shared** in the vista partition [.....] 

Sharing NTFS files alongside an Ubuntu distribution is problematic, at best.  Windows XP largely hid the sharing attributes from the user of windows XP by hiding a lot of the extended attributes of the NTFS file system and simply setting the file to be 'shared' by all.

Now you have windows vista and don't want your files to be shared, with other windows users.  However IF the (Ubuntu) kernel wrote the files not to be shared (as say root), then you as 'Administrator' or 'Fred' would not be able to see the files also (possiable wondering if they were copied at all), as they would be owned by a user called 'Root'.

So it is a **feature** not a bug.

---

### Post by ZankerH on 2009-10-19
A way to work around this is to set the file ownership and permissions to root and restricted before you copy it over:

```
#!/bin/bash
chown root file
chmod 700 file
cp file location
chmod 755 file
chown you file
exit
```

You may want to familiarise yourself with the UNIX-standard file permissions, see the man-page on chmod:

```
man chmod
```

---

### Post by entropy1 on 2009-10-19
I noticed the same thing:
[http://ubuntuforums.org/showthread.php?t=1095586](http://ubuntuforums.org/showthread.php?t=1095586)

For small amounts of data, there are two ways, other than telling Vista to undo sharing.
1) From Vista, drag the files or folders to a flash drive or external hard drive and then drag them back to the hard drive.
2) From Ubuntu, rather than copy to files or folders from the Ubuntu partition to the Vista partition, copy them to a flash drive or external drive.  Then, the next time you boot Vista, copy them to the Vista partition.

---

### Post by Mark Phelps on 2009-10-20
You're copying files between two very different filesystems, hosted by two very different OSs -- neither of which is natively able to implement the account permissions of the other.  So, when you copy files into the filesystem controlled by the "other" OS (whichever one, Vista or Ubuntu), your current OS tries it's best to apply the permissions you've chosen.

Sharing the Vista OS partition in read/write with Ubuntu is just asking for trouble.  You would do better creating a shared NTFS data partition. That way, if that partition's filesystem gets corrupted, you will still be able to boot into Vista to repair it.  If the Vista OS partition filesystem gets corrupted, you won't be able to boot into it to repair it.

---

### Post by jimbean on 2009-10-26
thanks again linux, ubuntu, gnu, i will try both methods sometime in the future but its good to know there is quality help in the computer world
and for free this is great 
i thought i was the only one that did that
no strings attached

---

