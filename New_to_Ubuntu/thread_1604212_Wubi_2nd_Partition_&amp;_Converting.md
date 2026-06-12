---
title: "Wubi 2nd Partition &amp; Converting"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Yavatar on 2010-10-23
I'll try to keep this general in nature as I'm not looking for the actual methods to do this, just the feasibility of doing it...


If I create a 2ndary NTFS partition from Windows (2000), can I direct Wubi to install an ubuntu distro there? Are there any major issues to doing this? It seems this isn't quite like installing a program to a certain destination.

Assuming I do this, can I later convert that partition to a ext4 partition and generate a true dual-boot?


Now as I sit writing this, I realize my original rationale for writing this doesn't make sense as I was thinking I'd have a ext4 partition already, but I won't if I start with Wubi. (I'm having problems using Live CDs and I just want to see how the distro works out, if it it will install and work using wubi instead.)

That said, would that work instead of creating a new ext4 partition later on and using the util? Assuming the answer is yes, would it just be causing a lot of headaches or assuming everything went smoothly, result in about the same effort and time switching over?

My other thought is a 2nd partition just for ubuntu would help reduce fragmentation issues.

Thank for your thoughts.

---

### Post by Hippytaff on 2010-10-23
wubi installs ubuntu inside windows...so its a good way to test ubuntu if you cant do the liveCD thing. you can always delete it by uninstallin wubi. if you decide to dual boot back up all you important stuff :-)

---

### Post by Yavatar on 2010-10-23
Well, I researched the issue and followed a number of results trying to figure this out...

There are innumerable references to converting NTFS to Ext file system. However, there is NO WAY to convert file systems. All the methods that say 'convert' mean 'format'. That's not converting, that's destroying. ;)

Why you can't convert I don't know. The only thing I found was someone saying the the file pointers worked different between the two systems. I would think that FAT32 would be easier to convert over, but there doesn't seem to be a lot on that either.

I would have thought someone would have figured out a way to create a util to convert it over after all these years...

---

### Post by Hippytaff on 2010-10-24
you could back everything up then convert (format) the drive

---

### Post by bcbc on 2010-10-24
You don't need a second partition for wubi. It's unnecessary (the whole point of wubi is that you don't need to partition). The size of the virtual disk determines the size available, not the partition it's on - and fragmentation issues are non-existent as the disk is fixed from when it's first created (defragment windows before installing).

So. 1. Install wubi on the windows partition.
2. Try it out.
3. When you want to convert it to a real install, migrate it to the new partition you created. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
(that way you won't lose anything).

---

### Post by Yavatar on 2010-10-28
Well, it was a good thought EXCEPT there is no way to convert from NTFS to a Linux file system (formatting doesn't count, that's destructive ;) ). So any points on why or why not I should do a separate p.artition become a point moot. I'm just rather surprised no industrious soul came up with a way to convert it over.

The main reason I wanted to do this is because I only have a 10g hard drive in it so I'm not sure at this point if I plan on wiping windows later and trying to avoid musical partitions later on. Of course now that I planned this all out I will wipe Windows later and this all became a lot of needless worrying. ;)

---

