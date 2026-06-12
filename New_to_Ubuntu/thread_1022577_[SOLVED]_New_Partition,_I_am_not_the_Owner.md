---
title: "[SOLVED] New Partition, I am not the Owner"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by teh_yodeler on 2008-12-27
So I've created a new primary partition, /dev/sda3.
Mountpoint /media/storage.

Problem is, I can't do anything with this partition.  I'm unable to write any files to it as I'm not the owner (I think).


Help!  I tried chowning, but it seems that I did something wrong.  What should I do?  I want to use this partition as a storage for music and videos.


Can anyone explain this to me?  the more specific and step-by-step the instructions, the better - I get lost pretty easy on the command line.

Thanks a lot!
-----------------------
^^^^^^^^^This was my earlier post.  I followed the instructions given, and successfully mounted my "storage" partition.  This worked successfully for many restarts, and the partition was mounted automatically at startup.

Now, however, I can't access the partition.  It doesn't show up under "Places" like it used to, and I have no idea how to get it there.  This started just this morning and persists after restart.  I tried this:
```
compaq@compaq-laptop:~$ sudo mount /dev/sda3 /storage
mount: /dev/sda3 already mounted or /storage busy
mount: according to mtab, /dev/sda3 is already mounted on /storage

```

but I guess it's already mounted?  I **really** need to access these files.  Can anybody help??

THX ALOT!

:lolflag:


UPDATE: For some reason it was changed from /media/storage to just plain /storage.  Works for me.

---

### Post by logos34 on 2008-12-27
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by teh_yodeler on 2008-12-27
SWEET!  Thanks a lot

:guitar:

---

### Post by teh_yodeler on 2008-12-28
Bump, if someone can help that would be great :(

---

### Post by taurus on 2008-12-28
What filesystem is /dev/sda3?  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```

---

### Post by teh_yodeler on 2008-12-28
Ok everybody, I fixed it... Sort of.  For some reason, instead of being under media/storage, it is now just under /storage.  Oh well, that works for me... But i have **no idea** why it was changed.

Thanks taurus for the quick response

---

### Post by taurus on 2008-12-28
How did you mount /dev/sda3?  Do you have an entry in /etc/fstab to mount it to /storage instead of /media/storage?

---

### Post by teh_yodeler on 2008-12-28
This is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6e29f443-aa87-48bb-bb33-e7ba580139c0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c7ce4153-b602-48de-80b0-a9da6c7bd5ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /storage ext3 defaults 0 0
```

So I guess it does look like it's just under /storage... But I swears, for at least five restarts, it was mounted under /media/storage.

:confused::confused::confused:

lol.  I just put /storage under a bookmark so it's easy to find.  problem solved, but mystery.... unsolved!! haha

---

### Post by taurus on 2008-12-28
Well, you can always change it to look like this in /etc/fstab if you wish.

```
/dev/sda3 /media/storage ext3 defaults 0 0
```
And of course, you have to create a new mount point for it.

```
sudo mkdir /media/storage
```
Then, you need to change the ownership of /media/storage from root to your username so you can write to it anytime you want.  And if you use /media/storage as the mount point for that partition, there should be an icon on your desktop so you can just click it to access that partition.

---

### Post by teh_yodeler on 2008-12-28
Thanks!

:)

---

