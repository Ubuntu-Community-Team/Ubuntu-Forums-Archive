---
title: "cannot delete duplicate system file on seperate partition"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by decomp on 2009-05-28
Hello all!

I have file on a second partition that I am unable to delete even as root.
Sorry this is a bit lengthy but I don't know how else to explain.

I have my computer set up with a partition for ubuntu system and a partition for my home directory. I mucked up my ubuntu install when I didn't have a live cd to reinstall from, so I tried to reinstall using unetbootin from my second partition (normally my home partition.) That didn't work (got stuck in some kind of loop at the partitioning stage) so once I got around to getting an install cd again I reinstalled ubuntu from that. Problem was that if I tried to use my second partition as my home directory again, after install ubuntu would just boot into a blank screen. So I deleted all personalized home directory files except for my music & documents, which I placed in a seperate folder. reinstalled again, to no avail. I discovered the file extlinux.sys, which I believe is left over from the failed unetbootin install, lingering on this second partition. I tried to delete it but even as root i get:

```

decomp@decomp-laptop:/media/disk$ sudo rm extlinux.sys
[sudo] password for decomp: 
rm: cannot remove `extlinux.sys': Operation not permitted

```
I would really like to change my home directory back to this partition, but while this file is lingering I know I will always be booting into a blank screen. Can anyone help me?

Please let me know if theres any information you would like about my system

basic info: ubuntu jaunty 9.04 on a sony vaio pcg-v505 laptop.

Thank's for reading!

D

---

### Post by Paqman on 2009-05-28
Try:
```

sudo rm -f extlinux.sys

```

---

### Post by decomp on 2009-05-28
> **Paqman said:**
> Try:
```

sudo rm -f extlinux.sys

```

Hi Paqman,

I tried that with the result:

```

decomp@decomp-laptop:/media/disk$ sudo rm -f extlinux.sys
[sudo] password for decomp: 
rm: cannot remove `extlinux.sys': Operation not permitted

```

---

### Post by decomp on 2009-05-28
Oh I should also mention that I have tried to delete the files graphically by gksudo-ing nautilus, with the result that when I try to delete the file i get:

Error deleting file.
There was an error deleting extlinux.sys.
Error removing file: Operation not permitted.

Any more ideas?

---

### Post by michy99 on 2009-05-28
Have you tried deleting it from a Live CD?

---

### Post by decomp on 2009-05-29
> **michy99 said:**
> Have you tried deleting it from a Live CD?

Hi Michy99,

Yes I have, with the same results as listed above.

---

### Post by mikechant on 2009-05-29
Maybe the filesystem is corrupt?

It's worth running a filesystem check - you'll need to unmount the partition and then check it, you can do this in a gui way with the 'gparted' utility, or using the umount and e2fsck commands in a terminal if you prefer.
After the fsck try the delete again.

If this doesn't work, you could try 'delete by inode number' which is described here: [http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html](http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html)

---

### Post by decomp on 2009-05-29
> **mikechant said:**
> Maybe the filesystem is corrupt?

It's worth running a filesystem check - you'll need to unmount the partition and then check it, you can do this in a gui way with the 'gparted' utility, or using the umount and e2fsck commands in a terminal if you prefer.
After the fsck try the delete again.

If this doesn't work, you could try 'delete by inode number' which is described here: [http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html](http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html)

Hi mikechant,

thanks for your suggestions.

I unmounted the partition and ran a file system check in gparted, which came out fine.

I tried the guide you suggested to 'delete by inode number' with the following results.

```

decomp@decomp-laptop:/media/disk$ stat extlinux.sys
  File: `extlinux.sys'
  Size: 13312     	Blocks: 32         IO Block: 4096   regular file
Device: 803h/2051d	Inode: 269911      Links: 1
Access: (0444/-r--r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-05-29 16:42:19.000000000 -0600
Modify: 2009-05-22 16:51:52.000000000 -0600
Change: 2009-05-22 16:51:52.000000000 -0600
decomp@decomp-laptop:/media/disk$ sudo find . -inum 269911 -exec rm -i {} \;
rm: remove regular file `./extlinux.sys'? y
rm: cannot remove `./extlinux.sys': Operation not permitted 

```

I just keep getting 'operation not permitted' at every turn. :/

---

### Post by The Cog on 2009-05-29
Maybe it has some extended attribute set? Have a look with **getfacl extlinux.sys**

---

### Post by decomp on 2009-05-30
> **The Cog said:**
> Maybe it has some extended attribute set? Have a look with **getfacl extlinux.sys**

Hi The Cog,

results of getfacl are

```

decomp@decomp-laptop:/media/disk$ getfacl extlinux.sys
# file: extlinux.sys
# owner: root
# group: root
user::r--
group::r--
other::r--

```

---

### Post by decomp on 2009-06-02
I would like to ask the admins if there is no resolution offered in this forum if I am allowed to repost this question in the general ubuntu help section?

---

