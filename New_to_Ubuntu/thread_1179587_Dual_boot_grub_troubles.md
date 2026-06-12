---
title: "Dual boot grub troubles"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by darkwalt on 2009-06-05
Ok, so the down low is that I had a sata drive that failed, so I had to throw in an old IDE drive.  Now I have a replacement sata drive, and I want to have it visible in grub.  I decided to do a clean install on both the IDE drive and the sata drive.  The IDE drive contains jaunty, which I installed while the sata drive was disconnected.  I then installed win7 on the sata drive while the IDE drive was disconnected.  

I then tried adding the standard windows stanza to /boot/grub/meun.lst , but then I got an error.  I looked over my mobo bios just to make sure that the sata drive was detected, which it was.  Then I went and checked the forums.  I found [this page](http://ubuntuforums.org/showthread.php?t=1178468&highlight=hd0+hd1+hd2) to check the boot map.  

```

(hd0)	/dev/sdb
(hd1)	/dev/sdc
(hd2)	/dev/sdd
(hd3)	/dev/sde
```

I can mount my sata drive as a writeable drive within the GUI, and I know for a fact that it mounts as /dev/sda.  When I do a fdisk -ls I get this.
```
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd85b279

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4501    36149248    7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3a4e3a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2373    19061091   83  Linux
/dev/sdb2            2374        2482      875542+   5  Extended
/dev/sdb5            2374        2482      875511   82  Linux swap / Solaris

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe778e778

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2434    19551073+   7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000cd9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19457   156288321    c  W95 FAT32 (LBA)

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000ea36

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001    b  W95 FAT32

```

I have five drives connected to this machine.  Here is a list of their tasks.

sda: sata drive that I installed windows 7 on

sdb: ubuntu os drive

sdc: second ide drive.  Used for backups of windows since the last sata drive failed at least three times.

sdd: USB external drive.  Use that for storage of all ripped cd's and the like

sde: USB external enclosure hooked to a 500gb drive.  Used for backup of sdd and storage of non-important data.


At this point, i've been struggling with this for a few days here, and I frankly don't care what bootloader loads, I just want to get it working.  Does anybody have any suggestions?

---

### Post by lindsay7 on 2009-06-05
See if this works, I picked this off of another post that had a similar problem

sudo gedit /boot/grub/menu.lst

and add these lines

title              Windows 
root               (hd0,0)
savedefault
makeactive
map                (hd0)  (hd1)
map                (hd1)  (hd0)
chainloader        +1


It should be noted that there is a SPACE between (hd0) and (hd1) in both the 'map' lines. Otherwise, Grub responds with an error 11: unrecognized device string.

---

### Post by lindsay7 on 2009-06-05
I looked again and changed the root number, if windows is on sda it should be hd(0,0)

You may need to reset grub menu for the change in drive numbers, if so try this,

Do the following,


sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit

---

### Post by darkwalt on 2009-06-06
Ok, after trying both of your suggestions, neither one worked.  The first one gave me "invalid or unsupported file format", and the second one didn't do anything.  

Here is the output:
```

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub> 
```

I then did a 
```
gedit /boot/grub/device.map
```
and it showed the same thing.  I restarted and tried to boot from the windows entry in grub and nothing happened.  

Any other suggestions?  I'm open to reinstalling either one or both OSes if necessary, since I have both backed up.

---

### Post by logos34 on 2009-06-06
> **lindsay7 said:**
> 
title              Windows 
root               (hd0,0)
savedefault
makeactive
map                (hd0)  (hd1)
map                (hd1)  (hd0)
chainloader        +1


actually it should be:

> title              Windows 7
root               (hd**[COLOR="Red"]1[/COLOR]**,0)
savedefault
makeactive
map                (hd0)  (hd1)
map                (hd1)  (hd0)
chainloader        +1

or maybe grub/the bios sees it in third positition:

> title              Windows 7 
root               (hd**2**,0)
savedefault
makeactive
map                (hd0)  (hd**2**)
map                (hd**2**)  (hd0)
chainloader        +1

---

### Post by lindsay7 on 2009-06-06
Here is a guide and a lot of info on this subject, Hop it helps.

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by markbuntu on 2009-06-06
fdisk says sdb1 is the boot partition for windoze so in grub that would be hd(1,0). To keep things simple just add. I boot 6 OSs with nothing more than three lines each in grub.

title Windows7
root hd(1,0)
chainloader +1

It may be that the actual windows bootloader is not in the partition but in the first section of the drive so you can also try

root hd(0)

---

### Post by darkwalt on 2009-06-07
The correct answer was from logos34.

> **logos34 said:**
> or maybe grub/the bios sees it in third positition:


It did.  I can now boot win7 from grub.  Now I have to set the time it stays in the grub menu as longer.  Also, how do you set the thread as solved?  I've never had to do it before.

---

### Post by logos34 on 2009-06-07
can't mark threads a 'solved' anymore...dunno why...

you mean you want to increase the time the grub appears?

---

### Post by darkwalt on 2009-06-07
Yeah, how do I increase the time, and change the order that the items in grub appear?

---

### Post by logos34 on 2009-06-07
How'd you mark as '[Solved]'?  Just rename the thread?

Grub: 

--> **timeout** (in secs)

order in items they *appear on screen*:

just physically change them around, being careful to stay within the 'automagic' section.  If you want to change which one *boots first*, adjust **default **line

---

