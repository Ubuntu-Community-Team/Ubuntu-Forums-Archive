---
title: "What is this mystery partition?"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Inisfad on 2010-08-03
I am in the process of (trying) to create an image of my hard drive.  In doing so, I have come across a 'mystery' partition.  I basically set up my computer with a Ubuntu partition (9.10), a Windows partition and some unallocated space.  I notice listed separately from the above partitions a small ext2 partition with about 1gb in it.  I would like to view the actual files in this.  fdisk -l shows this as part of my Linux system, but I can't figure out what it is.  Any suggestions (and simple, please...still learning!)  Thanks

---

### Post by giddyup306 on 2010-08-03
> **Inisfad said:**
> I am in the process of (trying) to create an image of my hard drive.  In doing so, I have come across a 'mystery' partition.  I basically set up my computer with a Ubuntu partition (9.10), a Windows partition and some unallocated space.  I notice listed separately from the above partitions a small ext2 partition with about 1gb in it.  I would like to view the actual files in this.  fdisk -l shows this as part of my Linux system, but I can't figure out what it is.  Any suggestions (and simple, please...still learning!)  Thanks
It's probably your swap.

---

### Post by dv3500ea on 2010-08-03
Yeah, it will be your swap partition.

This is like the virtual memory page file in Windows.

It is for the operating system to use as 'virtual RAM' when the RAM is full or to hibernate to.

---

### Post by tarps87 on 2010-08-03
Could you post the output of fdisk -l please, the swap partition is usually formatted a special swap and labelled so. The output of fdisk should clear this up.

---

### Post by Inisfad on 2010-08-03
Ah, it's not the swap file.  I am able to identify that.  Here is the printout: 255 heads, 63 sectors/track, 30401 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x021b021a     Device Boot      Start         End      Blocks   Id  System /dev/sda1           15436       22888    59866222+  83  Linux /dev/sda2   *           1       10430    83778943+   7  HPFS/NTFS /dev/sda3           22889       30401    60348172+   5  Extended /dev/sda5           22889       30089    57842001   83  Linux /dev/sda6           30090       30401     2506108+  82  Linux swap / Solaris  I am curious as to what sda1 is.  It is listed as ext2, 969 mb used.  I can understand the rest of the above.   I originally partitioned my drive (as a newbie of course, so probably not done very well) with Windows XP (sda2 above), Ubuntu (sda5 above + sda 6 for swap, so all apparently under sda3 as 'extended'), and left 30gb or so unallocated next to Windows (in gpart) and about 50 or so unallocated next to Ubuntu.  It appears now that the unallocated Ubuntu area is now being used by something.  I think.  I am getting more confused as I think of this.  I was just hoping there was some easy way to see what that 1gb in sda 1 is.   Thanks for your help.

---

### Post by dv3500ea on 2010-08-03
> **Inisfad said:**
> I was just hoping there was some easy way to see what that 1gb in sda 1 is.   Thanks for your help.

If you run Applications -> Accessories -> Terminal and enter:
```

sudo mkdir /media/sda1 && sudo mount /dev/sda1 /media/sda1

```
A drive called 'sda1' should appear on your desktop and in the Places menu, that you can explore.

---

### Post by Keen101 on 2010-08-03
It's probably a recovery partition.

I bought a Hpmini netbook a while back, and it had a hidden ~1Gb Fat32 partition to reinstall the HP linux to factory default.

If you set the partition as not hidden in gparted, you should then be able to easily mount it in ubuntu and get to the files.

---

### Post by tarps87 on 2010-08-04
Quick format
> **Inisfad said:**
> Ah, it's not the swap file.  I am able to identify that.  Here is the printout:
```
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x021b021a
Device Boot      Start         End      Blocks Id  System
/dev/sda1           15436       22888    59866222+  83  Linux
/dev/sda2   *           1       10430    83778943+   7  HPFS/NTFS
/dev/sda3           22889       30401    60348172+   5  Extended
/dev/sda5           22889       30089    57842001   83  Linux
/dev/sda6           30090       30401     2506108+  82  Linux swap / Solaris

```
I am curious as to what sda1 is.  It is listed as ext2, 969 mb used.  I can understand the rest of the above.   I originally partitioned my drive (as a newbie of course, so probably not done very well) with Windows XP (sda2 above), Ubuntu (sda5 above + sda 6 for swap, so all apparently under sda3 as 'extended'), and left 30gb or so unallocated next to Windows (in gpart) and about 50 or so unallocated next to Ubuntu.  It appears now that the unallocated Ubuntu area is now being used by something.  I think.  I am getting more confused as I think of this.  I was just hoping there was some easy way to see what that 1gb in sda 1 is.   Thanks for your help.

Yes there is, see dv3500ea post.
Also can you post the output of the command mount please, lets see if it is in use

---

### Post by Inisfad on 2010-08-04
Thanks for all your responses.  I have mounted this, and as a result my 61gb Linux partition mounts on my desktop.  When I click on this, the file browser shows a file called 'Lost and Found' with an X written over the file icon.  I click on this, and I'm advised that the folder contents cannot be displayed, as I do not have permission necessary to view them.  The mystery continues.  Thanks so much for your feedback. (PS.  Is there any one place that lists many of these Linux instructions, or do most newbie Linux users just query as each problem comes up, to get whatever code needed for what they want to do.  For example, the code that dv3500ea has written above.  As I see it, I can understand what I am telling the computer to do.  But I would not have been able to ascertain this code myself.  Where/how do you learn these codes?)

---

### Post by muteXe on 2010-08-04
If you do a 
```

gksudo nautilus

```
you shuld be able to browse into it. But be careful, that's opening your file browser with root priviledges.

I know a some of the command line. I learnt it from making mistakes and the good people on this forum.

---

### Post by ezsit on 2010-08-04
A great place to start reading is:

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by Inisfad on 2010-08-04
Great link....Thanks!!!

---

