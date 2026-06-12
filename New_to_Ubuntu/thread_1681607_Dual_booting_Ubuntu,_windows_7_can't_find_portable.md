---
title: "Dual booting Ubuntu, windows 7 can't find portable HDD?"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by SlightlyChaotic on 2011-02-04
So I recently got a new portable hard drive. (Seagate Freeagent, 750 gb [here's a link.]("http://www.seagate.com/www/en-us/products/external/external-hard-drive/portable-drive/")) I figured "Nice, I'll try dual-booting ubuntu.

I followed an online tutorial or two, downoaded the ubuntu .iso, ran the disc, got ubuntu installed on the portable HDD, blah blah blah, everything worked out fine.

Until I tried to get to the disc on windows 7. I was thinking that I'd still be able to access the HDD on windows after I installed ubuntu on it, but it's not showing up under "my computer."

Just to see, I took the harddrive to a windows xp computer and the same problem exists. Ubuntu loads fine on that, too.

Thinking the problem was with partitioning (which it still might be) I re-installed ubuntu and told it to wipe and use the whole drive. That didn't help.

So, here's my question: Accessing that drive on windows is pretty important to me, so how do I do it? I don't know if the problem is that it's been re-formatted or if it's got something to do with partitioning, but how do I access it on windows now?

Preferably, I'd like to be able to access it on windows and run ubuntu as well, but if that's not possible, then I'd like to just use it on windows and I'll run ubuntu off of something else.

Thanks.

---

### Post by leviathan8 on 2011-02-04
Did you used the whole hard disk drive to install ubuntu on it? If yes, have you selected the ext3 partition type? If yes, windows is unable to see it.

---

### Post by NFblaze on 2011-02-04
As Leviathan said you are probrably using the EXT3 or EXT4 filesytem. Windows can only read FAT and NTFS filesytems natively.

---

### Post by SlightlyChaotic on 2011-02-04
So if I re-install ubuntu and use FAT or NTFS, everything should work OK?

EDIT: Tried that, and here's what happened: I don't see an NTFS option in the ubuntu partitioning menu, so I tried FAT32 and set the mount point to /windows, but then the installation said that it couldn't continue with the partitioning. What am I doing wrong?

So I have:
5 gb ext4 mounted at /
5 gb ext4 mounted at /boot
15 gb swap space
the rest is FAT32 mounted at /windows.

---

### Post by BHEJU on 2011-02-04
Here is a workaround. You can install a program in Win machine to be able to read Linux filesystems (ext-2-3-4).
It is called EXT2fsd ([http://www.ext2fsd.com/](http://www.ext2fsd.com/)).

This should work.

Cheers :)

---

### Post by JayKay3OOO on 2011-02-04
To answer your question (although BHEJU's answer is prob best for you)

/  - is root
/windows - never work because you are trying to mount windows parition inside of your root partition and it's saying 'I can't mount FAT32 inside EXT3'

So create the partitions to install ubuntu.

For the space you want as FAT32 simply right click on the remaining space and choose  FAT32 filesystem and create the partition. No need to assign a path or anything.

You can also make this new partition once you have installed and find the disks manager and do the same thing. At this point you should certainly have an option for NTFS even if for some odd reason it was not there during install.

---

### Post by SlightlyChaotic on 2011-02-04
Thanks for the help guys, here's what I ended up doing:

Bheju and JayKay's methods both look like they would have worked cleaner, but I ended up just setting up Ubuntu's partitions, and then partitioned the rest off and put (instead of FAT32) "Do not use partition." Then, when I plugged it into windows after ubuntu was installed, windows asked if I wanted to format that partition to NTFS, which I did. Ubuntu boots just fine and now I've got my hard drive back.

Thanks again!

---

