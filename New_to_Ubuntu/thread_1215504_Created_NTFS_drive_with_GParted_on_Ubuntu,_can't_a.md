---
title: "Created NTFS drive with GParted on Ubuntu, can't access in windows?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Scribbs on 2009-07-17
I formatted my drive as NTFS with Gparted in Ubuntu, then when I tried to access it in XP it showed up as a Healthy GPT Partition. After a few hours of googling etc I tried using the ext2 drivers which did nothing, and read somewhere that XP 64bit can access GPT partitions.

Now I've installed XP 64 and the same drive is showing up as an EFI Drive with no sight of an NTFS drive on it, yet if I boot into Ubuntu the drive shows up as NTFS and I have full access too it?

Anyone know how I can get access to the drive without losing all the data?

---

### Post by uberlube on 2009-07-17
1) did u make sure u specifies it as NTFS before partitioning?

2)did u give it a label?

---

### Post by Scribbs on 2009-07-17
Yes, it is an NTFS drive, and I have given it a label.

---

### Post by uberlube on 2009-07-17
hmm odd. it should recognize the partition automatically. Lets see the output of
```
sudo fdisk -l
```

---

### Post by HavocXphere on 2009-07-17
What does the disk manager say in windows. (Under Admin tools)?

---

### Post by Scribbs on 2009-07-17
Disk0; Layout: Partition, Type: Basic, Status: Healthy (EFI System Partition)

This was the same in XP32, except EFI was replaced with GPT.

I'm currently running Windows Update, I'll boot into Ubuntu afterwards and run fdisk -l

---

### Post by Scribbs on 2009-07-17
Device Boot: /dev/sda1, Start: 1, End: 121602, Blocks: 976762583+, Id: ee, System: GPT

and in Gparted it says

Partition: /dev/sda1, File System: NTFS, Label: CuddyNTFS, Flags: boot

---

### Post by uberlube on 2009-07-17
if it is just a media partition with no system files on it u dont need the bootflag.

---

### Post by Scribbs on 2009-07-17
So what flag should I use? I've tried setting it to msftres or whatever it was and now no partitions show up in XP at all.

---

### Post by uberlube on 2009-07-17
dont use any flag

---

### Post by adepoyu on 2011-05-26
Hi,

I would like to know how the story ended, because I am having the same problem here. I create an NTFS partition in a GPT disk with GParted but when I boot Windows 7 and go to disk management it always asks me to initialize the disk, and if I do so, Ubuntu does not recognize the GPT disk.
Any help would be very welcomed, as I have been googling for hours.

Many thanks

---

### Post by srs5694 on 2011-05-26
Adepoyu, please run the following commands:

```

sudo apt-get install gdisk
sudo gdisk -l /dev/sda
sudo fdisk -lu /dev/sda

```

Change "/dev/sda" in the second and third commands to the disk device that holds the partition in question, if it's not /dev/sda. Post the complete output here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags.

My suspicion is that you might have a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) with mismatched GPT and MBR partitions. This could easily produce the symptoms you describe. If so, the mismatch will be obvious when comparing the two partition tables.

---

### Post by adepoyu on 2011-05-27
Hi srs5694,

I am glad you reply cause yesterday just after I posted, I found a thread with a problem similar to the one I have and they said you may know the solution.
Anyway, I have opened a new thread with the results of the code you mention.

Thanks.

---

