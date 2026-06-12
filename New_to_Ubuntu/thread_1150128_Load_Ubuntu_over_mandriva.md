---
title: "Load Ubuntu over mandriva"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by crew51m on 2009-05-05
I want to put 9.04 on my dual boot hard drive. It now has mandriva\vista, it boots fine, in both, how do I load ubuntu over mandriva? Will Ubuntu reformat the partition, delete mandriva and load ubuntu without disturbing vista? I need to keep vista for files I need. 

Thanks.

---

### Post by tjwoosta on 2009-05-05
i would use gparted to delete the mandriva partition and leave it as unallocated space

then when you go to install ubuntu you can choose "use largest continuous free space" and it will install ubuntu to the unallocated space that you made

---

### Post by blueridgedog on 2009-05-05
Ubuntu will not delete the partitions, but you can install over them and elect to format them as you do.  If you post:

```
sudo fdisk -l
```

or fdisk -l as root (from Mandriva) then we can give you some advice as to how to install Ubuntu and manually setup the partitions.

---

### Post by crew51m on 2009-05-05
Thanks. Is gparted in vista?

---

### Post by raymondh on 2009-05-05
> **crew51m said:**
> Thanks. Is gparted in vista?

gparted is the partition editor in Ubuntu.  You can use the live CD.  Go to system > administration > partition editor.

When using the live cd, your HD is not mounted ... shouldn't be.  Just to be sure though, whilst in live session mode and you see your HD on the desktop, go ahead and unmount it (right click > unmount).

You can also download gparted.  It's a valuable tool to have around

---

### Post by lkraemer on 2009-05-07
Crew51m,
You didn't say, and everyone assumes, that Vista is on the first partition. Is this the case?  Just make sure you know, without a
doubt which partition Mandriva is installed on.  

I'd suggest downloading a LiveCD of Gparted, SuperGrub, UBCD, Clonezilla, and SystemRescueCD.

Use Google to search for these strings: "Gparted, Supergrub au,
Dual Boot au, UBCD, Clonexilla, and SystemRescueCD"

Then burn the ISO's as Disk at Once (DAO) and at 4x or 8x speed.  After
that boot the LiveCD of gparted and delete the partition of Mandriva.

Remember: There is a MAXIMUM of 4 Primary Partitions on any one Physical
Hard Drive.....so, if Vista is first, and the recovery partition (typically at the end of the layout) is two, you have two for Ubuntu......ie, Root and Linux-Swap.  GREAT!  Swap should typically be
2x of RAM......so that sizes the remainder for Ubuntu.
(Note: I typically move the Recovery Partition immediately after the
Vista Partition, because that is where Vista typically puts it.

If Vista was first, Ubuntu will install, and I always use Manual for setting up the partitions, but that is my choice.

Good Luck.

lkraemer

---

### Post by crew51m on 2009-05-07
I figured it out, I loaded ubuntu and ran the partition editor, it showed the partitions and where to put Ubuntu, I deleted the mandriva part, loaded ubuntu, and am now dual booting with no problems. Vista fixed what ever problems there are. I now only have a choice of Ubuntu or vista, which is what I want. 

Thanks for the help.

---

