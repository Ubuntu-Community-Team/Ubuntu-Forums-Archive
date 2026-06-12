---
title: "using multiple sata external hard drives"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by josephmills on 2011-02-23
Hi there, before I start I would like to say that I am very new to ubuntu, that being said here is my problem.   
          So I am using a masscool external hard drive. Here is a link to the type of masscool that I am using.        [http://www.masscool.com/product_detail.php?tab=2&pid=&id=70#p](http://www.masscool.com/product_detail.php?tab=2&pid=&id=70#p)

          Here is the problem that I am having. I use to have 2 ibm t30 that came with a 40 gig hard drive the video card went out on both (t30's)and snow I am trying to salvage the hard drives using the masscool .  When I hook up the mass cool with say hard drive #1 It worked out of the box. But when I hook up hard drive #2 it wont show up. So i go to 
System->Administration->Disk Utilities  
I see that the os sees the hard drive. but the info is all wrong when I try to reformat the hd. In hd#2 it wont let me (see attachment)I get error messages.:confused:   what to do next ?
do I have to make a separate mounting point? I would like to thank the people that read this and the ones that post Thank You

---

### Post by TeoBigusGeekus on 2011-02-23
Is it unmounted when you tried to format it?

---

### Post by Gixxy on 2011-02-23
do you have 2 of the masscool externals? 
Try the known working one on the machine

Are there 2 machines? 
Maybe try a different usb port.

...Cringe... see if it works on a windows machine?

Sometimes external enclosures foo up.

---

### Post by josephmills on 2011-02-23
no I don't think so on hard drive #2 on hard drive #1 it mounted itself "out of the box" . This is where I am getting confused do I have to mount harddive #2 in  a directory and then if I have say hard drive #3 then do I mount that in different directory or in the same directory as HD #1 ?

---

### Post by josephmills on 2011-02-23
> **Gixxy said:**
> do you have 2 of the masscool externals? 
Try the known working one on the machine

Are there 2 machines? 
Maybe try a different usb port.

...Cringe... see if it works on a windows machine?

Sometimes external enclosures foo up.



no I open the masscool and pull the sata drive out of the pin brace then put the other one in. no on the windows I called mass cool and sat on the phone for hours to nothing. what do you mean by "foo"?

---

### Post by Gixxy on 2011-02-23
I got ya... are you sure that 40gb was good when you pulled it?

And again with that 40gb does it work in the enclosure on another machine?

---

### Post by josephmills on 2011-02-23
> **Gixxy said:**
> I got ya... are you sure that 40gb was good when you pulled it?

And again with that 40gb does it work in the enclosure on another machine?




hd #1= works in both machine 1, virtual windoz and on machine 2 and on a live dvd(bt4) 
hd #2 same thing on both machines and not readable in my virtual box 
and not reading on a live cd

---

### Post by Gixxy on 2011-02-23
> **josephmills said:**
> hd #1= works in both machine 1, virtual windoz and on machine 2 and on a live dvd(bt4) 
hd #2 same thing on both machines and not readable in my virtual box 
and not reading on a live cd

So I am guessing by this you are say that HD#2 is not working at all, with anything. Seems to be a drive issue.

You could try to attach the drive internally to eliminate any issues with the enclosure.

or 

Try to mount the drive manually.


```
sudo fdisk -l
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc81f6a63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10453    83962698+   7  HPFS/NTFS
/dev/sda2           10454       38913   228604950    5  Extended
/dev/sda5           10454       38542   225624861   83  Linux
/dev/sda6           38543       38913     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006bd94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312571192    7  HPFS/NTFS

My external is /dev/sdb1

```
 sudo mount /dev/sdb1 /"mount point"
```

Mine is mounted at /media/music

---

### Post by josephmills on 2011-02-23
> **Gixxy said:**
> So I am guessing by this you are say that HD#2 is not working at all, with anything. Seems to be a drive issue.

You could try to attach the drive internally to eliminate any issues with the enclosure.

or 

Try to mount the drive manually.


```
sudo fdisk -l
```Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc81f6a63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10453    83962698+   7  HPFS/NTFS
/dev/sda2           10454       38913   228604950    5  Extended
/dev/sda5           10454       38542   225624861   83  Linux
/dev/sda6           38543       38913     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006bd94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312571192    7  HPFS/NTFS

My external is /dev/sdb1

```
 sudo mount /dev/sdb1 /"mount point"
```Mine is mounted at /media/music





ok so after I typed in fdisk -l I got a to the bottom of the command  and it says 
Disk /dev/sdb doesn't contain a valid partition table

how do I make it into a  valid partition table?

---

### Post by Gixxy on 2011-02-24
I think you may have a bad drive...

Anyone else want to add to this?

---

### Post by josephmills on 2011-02-24
lets get this party, "bump"in turn up the volume.

---

### Post by josephmills on 2011-02-24
Ok,so I made a video here it is 


[http://www.youtube.com/watch?v=O9vlxXRunCQ](http://www.youtube.com/watch?v=O9vlxXRunCQ)

---

### Post by TeoBigusGeekus on 2011-02-24
Do you have any crucial data on the drive?
If not, fire up gparted
```
gksu gparted
```
and format it.

---

### Post by josephmills on 2011-02-24
which drive? #1 has data that I need #2 has nothing that I need #3 has nothing that  *need. *

---

### Post by josephmills on 2011-02-24
oK,so i went to gparted and the format was greyed out I tried to create a partition but I got an error message saying that It could not do that :confused:   this was all done with hd #2 and #3

---

