---
title: "fdisk doesn't see NTFS partition correctly"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Go_Big_Blue on 2010-01-09
Okay - so I built me a nice little desktop unit with several hdd's on it.  Why? Just because.  At any rate, I have an NTFS partition that doesn't show up correctly in fdisk that I am trying to mount.  When I use the partition editor, it shows it as an ntfs partition, but when I use fdisk, it shows it as a FAT16 partition.  Any thoughts? (Pic and fdisk output below.)



```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc99cc99d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       45894   368643523+   6  FAT16

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8973aa38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       40412   324609358+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f8c6f8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       11473    92156841    7  HPFS/NTFS
/dev/sdc2           11474       13844    19045057+  83  Linux
/dev/sdc3           13845       14837     7976272+   5  Extended
/dev/sdc5           13845       14837     7976241   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000
```

---

### Post by J V on 2010-01-09
> Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       40412   324609358+   7  HPFS/NTFS

[http://www.readingglasses.com/](http://www.readingglasses.com/)

---

### Post by Go_Big_Blue on 2010-01-09
> **J V said:**
> [http://www.readingglasses.com/](http://www.readingglasses.com/)

Ha-Ha-Ha, very funny. :o  But back at you!!  Check out the partition on the image, /dev/sda1.

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       45894   368643523+   6  FAT16
```

Maybe it would have helped you if you would have looked at the attached image of the partition editor?  :D

---

### Post by J V on 2010-01-09
Mabey it would help you to buy reading glasses:

> ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc99cc99d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       45894   368643523+   6  FAT16

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8973aa38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       40412   324609358+   7  [B]HPFS/NTFS
[/B]
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f8c6f8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       11473    92156841    7  HPFS/NTFS
/dev/sdc2           11474       13844    19045057+  83  Linux
/dev/sdc3           13845       14837     7976272+   5  Extended
/dev/sdc5           13845       14837     7976241   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000
```> Maybe it would have helped you if you would have looked at the attached image of the partition editor?  :grin:

---

### Post by Go_Big_Blue on 2010-01-09
Okay J V - I guess I need to spell it out for you.

**/dev/sda1** is the drive in question, not **/dev/sdb1**.

I have 6 hdd's attached to this machine, several of which are disconnected at the moment.

/dev/sda1 is a 1.5TB hdd.  /dev/sdb1 is a 500GB hdd.  Both have a copy of WindowsXP Pro on them.  But I need to mount the /dev/sda1 drive so I can copy over the system32 file folder from the /dev/sdb1 hdd (which I am trying to trouble shoot as to why it won't boot.)

So again, maybe you should read ALL of the information and provide some useful help.  

Thanks.

---

### Post by J V on 2010-01-09
Perhaps you should look at the image, I'm not dyslexic and I'm pretty sure thats a b...

The sd part (solid drive?) means its a drive, the letter is which one, and the number is which partition, you are looking for sdb, not sda...

> /dev/sda1 is a 1.5TB hdd. /dev/sdb1 is a 500GB hddI gathered from the fdisk output... You also have an unformatted 320 GB disk (unless you cut the output) and a 160 GB disk which (unfortunatley) has more NTFS space than EXT space...

Click on places > computer and you should be able to open it, if not, (which happens occasionally on windows drives for no apparent reason) you can use the mount command to gain access...

---

### Post by Go_Big_Blue on 2010-01-09
Now that's funny!! :D

Okay, here is the image that I MEANT to attach to the post. :D

---

### Post by J V on 2010-01-09
ahh, ok... that is wierd... Since you are using karmic, could you open your palimpsest program (in admin menu) and check the differences between the two drives please?

Edit:
[quote=man fdisk]fdisk is a buggy program that does fuzzy things - usually it happens to produce reasonable results.[/quote]
Try cfdisk (read man first lol)

Edit2:```
sudo sfdisk -l /dev/sda
```

---

### Post by Go_Big_Blue on 2010-01-09
> **J V said:**
> ahh, ok... that is wierd... Since you are using karmic, could you open your **palimpsest program** (in admin menu) and check the differences between the two drives please?

Don't see a palimpsest program.  Is there another name that it goes by?

---

### Post by J V on 2010-01-09
aka disk utility :)

---

### Post by Go_Big_Blue on 2010-01-09
> **J V said:**
> 

Edit2:```
sudo sfdisk -l /dev/sda
```

Okay, ran the sfdisk -l command and this is what it came back with:

```
sudo sfdisk -l /dev/sda

Disk /dev/sda: 182401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  45893   45894- 368643523+   6  FAT16
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty 

```

---

### Post by falconindy on 2010-01-09
It's probably safe to assume the issue is somewhat related to the disk being formatted as NTFS in Windows and perhaps something was checked off that shouldn't have been (i.e. wasn't created as a simple volume).

I don't have anything truly constructive, except... As a last resort, you might try see what testdisk has to say. If it can correctly detect the 1.5tb partition, just ask it to rewrite the partition table.

---

### Post by J V on 2010-01-09
Well what can I say, you must be pretty good to get winXP running on FAT16 :P

Like I said, try the disc utility and see what exactly the differences are between the two NTFS parts

---

### Post by Go_Big_Blue on 2010-01-09
I think the easiest thing to do at this point is probably just wipe the whole partition, create a new one and then copy over the entire contents of /dev/sdb1 to /dev/sda1.  Don't want to spend too much time on it because I need to get into the reasons that the "other OS" is not booting up.

---

### Post by J V on 2010-01-09
wait, wasn't it the sdb1 that needed copying from sda1?

Don't get them mixed up or you can forgetaboutit :)

Also, if its the sda1 that won't boot, it seems we've found the culprit... Bad partitioning table...

---

### Post by Go_Big_Blue on 2010-01-09
> **J V said:**
> wait, wasn't it the sdb1 that needed copying from sda1?

Don't get them mixed up or you can forgetaboutit :)

Also, if its the sda1 that won't boot, it seems we've found the culprit... Bad partitioning table...


No - I need to copy sdb1 TO sda1.  But, I have another problem now.  I deleted the NTFS partition on sda1.  When I went to create a new partition on sda1, GPARTED wouldn't give me the option to select it as NTFS.  That option was grayed out (along with hfs, hfs+, jfs, reiser4, ufs and xfs).  Don't quite understand this.  I can select it as a FAT32 partition, but I need it to be an NTFS partition.  Any thoughts.

---

### Post by falconindy on 2010-01-09
Install the 'ntfsprogs' pacakge.

Too bad, I was curious what testdisk would do ;P

---

### Post by Go_Big_Blue on 2010-01-09
> **falconindy said:**
> Install the 'ntfsprogs' pacakge.

Too bad, I was curious what testdisk would do ;P

I'm not sure where I could find the 'ntfsprogs' package, so I downloaded the NTFS Configuration Tool, which provides a GUI for formatting and working with ntfs drives using the ntfs-3g tool.

Sorry about not using the testdisk thing, just super busy and thought the reformatting/copy option would be the fastest thing to do.

---

### Post by Go_Big_Blue on 2010-01-09
What about using ddrescue to make a bit for bit copy of /dev/sdb1?  Any thoughts on that one?

---

