---
title: "rhythmbox hates me and wants me to die? Thats kinda rude..."
date: 2009-08-27
forum: New to Ubuntu
---

### Post by ithinkitschad on 2009-08-27
What did I write wrong in my fstab? The Problem is that my secondary hard drive that should mount on its own when it boots ... Dot dot dot ... doesent seem to do that, -only for rhythmbox-. BTW, that lil Rhythmbox hates me/Wants me to die? Thats pretty rude and racist .... I'm sure this is an easy fix but I'm finding nothing on google(I didnt look, just help me out... People can find this on google later, so I guess I'm helping out. Actually were all helping out). Heres my fstab:
Did I forget something simple? If I did, forgive me and tell me what to write. But I deffinedtly love you all.

/dev/sdb        /media/disk     auto,rw,user,exec       0       0

Can I be honest? I never learned what that third row sh*t means. I just pick the things that seem important to what I'm using from the other rows... damn I'm lovable. Maybe just post a link for info, and tell me what I'm doing wrong. BTW that drive mounts on its own just fine, theres no other problems other than the fact that if I reboot, that damn drive doesent seem to exist to Rhythmbox for a couple of mins.. Whats up?

---

### Post by ithinkitschad on 2009-08-27
Hey people should add me as a friend too - if he/she is smart. That way some random person that you've never met (me) can bother you at all hours of the day/night with trivial questions.. its fun for you though.  
: )

---

### Post by NoaHall on 2009-08-27
Can I just tell you, I have no idea what you're talking about. I can't see your fstab, and I have no idea what's wrong.

---

### Post by scragar on 2009-08-27
> **ithinkitschad said:**
> /dev/sdb        /media/disk     auto,rw,user,exec       0       0


sdb is a block device(not what you want). You want sdb1 for the first partition on the hard drive.

```
/dev/sdb**1**        /media/disk     auto,rw,user,exec       0       0
```

---

### Post by kpkeerthi on 2009-08-27
> **NoaHall said:**
> Can I just tell you, I have no idea what you're talking about. I can't see your fstab, and I have no idea what's wrong.
+1

To the OP, this might help:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by ithinkitschad on 2009-08-27
> **NoaHall said:**
> Can I just tell you, I have no idea what you're talking about. I can't see your fstab, and I have no idea what's wrong.


It mounts just fine, but when I open rhythmbox (after a reboot) it starts removing all my music from it as it didn't mount. Then as it gets to the end it starts restoring it. I think thats usually after I've opened the folder in Nautilus. Witch is mounted just fancy fine perfect

---

### Post by ithinkitschad on 2009-08-27
> **scragar said:**
> sdb is a block device(not what you want). You want sdb1 for the first partition on the hard drive.

```
/dev/sdb**1**        /media/disk     auto,rw,user,exec       0       0
```

Damn, I just did that and was praying it would work. It didn't, thats a bummer. And to everyone else that wants to see the *other* lines of my fstab here you go

  GNU nano 2.0.9              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b6982aca-38a5-4ac6-b9e6-8ad6285e2b7a /               ext3    relatime,erro$
# swap was on /dev/sda5 during installation
UUID=a852bf16-43af-43c9-ad14-f32555bcd601 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/disk     auto,rw,user,exec       0       0

---

### Post by scragar on 2009-08-27
Huh, that's strange.
Try running this:
```
cat /proc/partitions
```
And post the output([noparse] ```
 and 
``` to display output in easier to read format[/noparse])

---

### Post by ithinkitschad on 2009-08-27
And if I didn't state the problem good enough... The drive mounts just fine, I can use it just fine. When I open rhythmbox it starts removing the imported folder on that drive. So does songbird and every other thing I've tried. I dont get whats wrong
p.s. I know ppl hate songbird

---

### Post by ithinkitschad on 2009-08-27
> **scragar said:**
> Huh, that's strange.
Try running this:
```
cat /proc/partitions
```And post the output([noparse] ```
 and 
``` to display output in easier to read format[/noparse])

   8        0    8257032 sda
   8        1    7855753 sda1
   8        2          1 sda2
   8        5     393561 sda5
   8       16   78150744 sdb
   8       17   78148161 sdb1


Thank you does that help?

---

### Post by NoaHall on 2009-08-27
I love songbird. Removing the imported folder? So it deletes the folder with music in or what? Or just can't play music from there?

---

### Post by rustutzman on 2009-08-27
You need to make sure the drive mounts to the same spot every time for Rhythmbox to keep the songs in place. You should address the drive by UUID or Label in fstab.

Russ

---

### Post by ithinkitschad on 2009-08-27
> **NoaHall said:**
> I love songbird. Removing the imported folder? So it deletes the folder with music in or what? Or just can't play music from there?

when you have any music player sonbird/winamp you choose a folder for it to import and find music on. It imports it and sees my music on my hd then when i restart it, it starts removing it like its not there. Its doing this with video too on anything i use. thats why i think its a prob with the fstab. but im pretty new to all this linux stuff so really i got no idea. and yea i love songbird too. its like firefox for music. not a bad idea

---

### Post by ithinkitschad on 2009-08-27
> **rustutzman said:**
> You need to make sure the drive mounts to the same spot every time for Rhythmbox to keep the songs in place. You should address the drive by UUID or Label in fstab.

Russ

Hey, I'm sorry but I dont really know what that means. Witch part should I change in fstab?
FYI, I'm googling UUID right now.

---

### Post by Cheezespread on 2009-08-27
Just wondering one thing. Please correct me if I am wrong . Needn't you specify what type of filesystem you are trying to mount through fstab ?

/dev/sdb1        /media/disk  (**vfat/ntfs-3g/ext3**)   auto,rw,user,exec       0       0

Or is it not mandatory?.

---

### Post by ithinkitschad on 2009-08-27
> **Cheezespread said:**
> Just wondering one thing. Please correct me if I am wrong . Needn't you specify what type of filesystem you are trying to mount through fstab ?

/dev/sdb1        /media/disk  (**vfat/ntfs-3g/ext3**)   auto,rw,user,exec       0       0

Or is it not mandatory?.

Oh, damn, I'm not sure but that sounds right, I did that for other ones

---

### Post by rustutzman on 2009-08-27
> **ithinkitschad said:**
> Hey, I'm sorry but I dont really know what that means. Witch part should I change in fstab?
FYI, I'm googling UUID right now.

Open a terminal and type blkid. This will give you the uuid for the drives. Take the uuid for sdb1 and set your fstab using it.
While you're at it type sudo fdisk -l and post the output of that too.

Create a directory as root in /media for the drive. ie
/media/music 

UUID=your uuid from above


example:
UUID=5AC556BE43 /media/music filesystem

Mine is as follows:
UUID=454CDA556B5E56E /media/MusicPhotos ntfs-3g umask=000 0 0

Russ

---

### Post by ithinkitschad on 2009-08-27
No, it doesn't have to do with putting the file system there. Somethings damn wrong though. This is why Linux is awesome? This is awesome ...

---

### Post by ithinkitschad on 2009-08-27
> **rustutzman said:**
> Open a terminal and type blkid. This will give you the uuid for the drives. Take the uuid for sdb1 and set your fstab using it.
While you're at it type sudo fdisk -l and post the output of that too.

Create a directory as root in /media for the drive. ie
/media/music 

UUID=your uuid from above


example:
UUID=5AC556BE43 /media/music filesystem

Mine is as follows:
UUID=454CDA556B5E56E /media/MusicPhotos ntfs-3g umask=000 0 0

Russ

Sorry, I'll try that. Hang on.










chunks@bob:~$ blkid 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="b6982aca-38a5-4ac6-b9e6-8ad6285e2b7a" TYPE="ext3" 
/dev/sda5: UUID="a852bf16-43af-43c9-ad14-f32555bcd601" TYPE="swap" 
/dev/sdb1: UUID="6e3d5ece-6d51-4878-8c15-97552c75d1e2" SEC_TYPE="ext2" TYPE="ext3" 
chunks@bob:~$ sudo fdisk -l
[sudo] password for chunks: 

Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034b93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         978     7855753+  83  Linux
/dev/sda2             979        1027      393592+   5  Extended
/dev/sda5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
chunks@bob:~$ 


*******************

So was that do-able? Because I didnt find out how to do it. Coo, I figured out smbfs weeks ago and found out how to mount a hd on a windows sys but i cant make my own drive mount. niiiiiiice.

---

### Post by rustutzman on 2009-08-27
Ok try this in fstab:
UUID=6e3d5ece-6d51-4878-8c15-97552c75d1e2 /media/music ext3 relatime 0 0

That should mount your drive as music or whatever you created in /media. If it did you will have to let Rhythmbox re-find your music. Once it does you should be good on Rhythmbox every time you boot.

Russ

---

