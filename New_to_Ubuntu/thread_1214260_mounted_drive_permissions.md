---
title: "mounted drive permissions"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Zenze on 2009-07-15
Hello everyone,

So if they answer to this is really obvious/simple feel free to slap me or something :p

Anyway I just got a new drive for my desktop, formatted to ext3, and am trying to get it set up correctly. Here is my current situation:

I made a mount point at /media/hdd2
with the permissions set to: drwxrwxr-x user user
and ran:
```
sudo mount -t ext3 /dev/sdb1 /media/hdd2
```

From my understanding that should mount the drive to /media/hdd2 with the same permissions as I set to that directory. However, after I mount the drive the permissions are changed to:
drwxr-xr-x root root
This is not what I want.

I have looked over multiple guides and examples and don't see what I am doing wrong or how to fix the problem. I know for my ntfs drive that in the fstab file I just added uid= and gid= as options. Is there something simular that I am supposed to do with this ext3 drive? It seems so simple... 

Thanks a bunch.

---

### Post by NightwishFan on 2009-07-15
I am not exactly filled with knowhow about permissions. However, on my backup partition, I change the permissions of the files themselves using chown.

Example:
```
sudo chown -R youusername /your/target
```
This command should alter every file contained in your target to be under your command. It should persist through mounts. However this is likely a very hack and slash solution.

---

### Post by Zenze on 2009-07-15
Ahh yea that did it... now I feel like a fool...

For some reason I remember not being able to change the permissions of a drive while it was mounted, but maybe that was just with NTFS.

---

### Post by NightwishFan on 2009-07-15
Glad you got it working. :p

---

