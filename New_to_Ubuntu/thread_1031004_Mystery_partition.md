---
title: "Mystery partition?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Andy06 on 2009-01-04
On a couple of ubuntu installs that I did, there seems to be a 500MB mystery partition that I have no idea about.

In all these installation I selected "Use largest continuous free space" or "Resize existing partition". I've attached a screenshot of what the partitions look like in the Vista disk management tool. Here it is 86 MB but in another installation it is 550 MB. The partition only contains one folder called "LOST+FOUND" which is inaccessible. As you can see from the attachment, it also seems to be formatted NTFS! (which is what the whole extended partition was before I put ubuntu on it, but apparently Gparted did not reformat this particular logical partition).

So what does this partition do? It's certainly not /boot or /home and the main ext3 partition [20.12 GB] and swap [941 MB] can be distinctly seen in the picture.C:, F: and D: have nothing to do with Linux.

P.S What's with all the partitions being marked as primary? All of the linux partitions are logical partitions within an extended partition.

---

### Post by Bucky Ball on 2009-01-04
Coupla things ...

Why are they all primary partitions? Windoze is all that needs this. Linux doesn't. Your data partitions - make one large extended partition and fill this with *logical* partitions/drives.

I would say Windoze needs the 86mb partition to keep track of what the disk is, what is on it and where. But I could be totally wrong.

---

### Post by jimmy the saint on 2009-01-04
Thats really strange.  Have you tried to access it so see what, if any, files are on it?

---

### Post by kansasnoob on 2009-01-04
I can't see that it matters much. It could just be the result of partitioning "rounding" to cylinders.

But you have yourself painted into a corner anyway. No physical drive will allow more than 4 primary partitions.

One extended partition counts as one primary and you can have many, many logical partitions inside one extended partition.

Basically you're done with that drive until you do some major repartitioning, cloning, reinstalling, etc.

---

### Post by Andy06 on 2009-01-05
> I would say Windoze needs the 86mb partition to keep track of what the disk is, what is on it and where. But I could be totally wrong.

I'm pretty sure its a Linux partition. Ubuntu created it, windows doesn't have anything to do with it. On another computer this same partition (550MB, ext3) is ext3, so windows couldn't be the one creating this.

>  Thats really strange. Have you tried to access it so see what, if any, files are on it? 

Yes. An inaccessible folder called LOST+FOUND with the linux mail emblem on it. 

> 
But you have yourself painted into a corner anyway. No physical drive will allow more than 4 primary partitions.

One extended partition counts as one primary and you can have many, many logical partitions inside one extended partition.

Basically you're done with that drive until you do some major repartitioning, cloning, reinstalling, etc.
1 Hour Ago 11:27 PM

No problem. Its all I need. A linux partition, a windows partition, a common data partition and a recovery partition.:D

---

### Post by Bucky Ball on 2009-01-05
> **Andy06 said:**
> I'm pretty sure its a Linux partition. Ubuntu created it, windows doesn't have anything to do with it.:D

Wasn't that 86Mb partition an NTFS? Linux ***will not*** create one of them. If it is NTFS, it was not created by Ubuntu.

---

### Post by theacerguy on 2009-01-05
it could be swap i think i have about a gig of swap i never actualy checked

---

### Post by Bucky Ball on 2009-01-05
Yep, 941mb would be the Linux swap. Drive G: though is a mystery. Tried deleting it and expanding the partition next to it?

---

### Post by Bucky Ball on 2009-01-05
.
Duplicate post.

---

### Post by Andy06 on 2009-01-05
> Wasn't that 86Mb partition an NTFS? Linux will not create one of them. If it is NTFS, it was not created by Ubuntu. 

Its NTFS in this one because I had an empty partition which was formatted NTFS which I asked ubuntu to use, so it left this partition unformatted but used it for something nevertheless. 

This same mystery partition is there on other computers as well and is formatted as ext3, so certainly a Ubuntu Linux thing. This partition varies from size from 86 to 700 MB, always containing the Lost+found folder, once again a linux folder since it has a linux specific emblem to it.

> it could be swap i think i have about a gig of swap i never actualy checked 

Don't think so, the swap partition can be clearly seen after the ext3 partition and by default ubuntu creates it after the main partition, this one is before the main partition.

> Yep, 941mb would be the Linux swap. Drive G: though is a mystery. Tried deleting it and expanding the partition next to it? 

I am too scared. What if Windows or Linux are using it to record and identify all the logical partitions within the extended partition. That could be it but sometimes this partition is only 25-30 MB whereas sometimes it is 700 MB on some computers. And it always has this Lost+Found folder, what is this??:D

---

### Post by Bucky Ball on 2009-01-05
Try this:

```
locate lost+found
```What does it look like? Post it here. This is mine.

```
/lost+found
/boot/lost+found
/home/lost+found
/usr/sbin/mklost+found
/usr/share/man/man8/mklost+found.8.gz
```

You could have one missing from your /home directory.

---

### Post by Andy06 on 2009-01-05
```
/lost+found
/usr/sbin/mklost+found
/usr/share/man/man8/mklost+found.8.gz
```

Note I do not have separate /home and /root partitions. My installation has 3 partitions:

1) /
2) Swap
3) Mystery partition

Does this command search other partitions as well? It seems to have found all lost+founds in this partition.

The location in properties shows /media/disk but that is merely the mount point I assume.

I also did a bit of research and the folder is meant for chkdisk/fdisk to recover corrupt files to, but even then it doesn't explain why it has its own sweet partition and isnt in the main partition as is the norm.

Plus this has been happening on multiple computers, so its not an isolated problem.

---

### Post by Bucky Ball on 2009-01-05
Places->File System->Home

What ya got? No Home folder?

---

### Post by The Cog on 2009-01-05
It looks to me like Windiws is telling you there are 5 primary partitions, which is not possible. Therefore, you can't trust it. Use Ubuntu and use the command ```
sudo fdisk -l
``` to see what's really there.

---

### Post by Andy06 on 2009-01-05
> Places->File System->Home

What ya got? No Home folder? 

There is no file system under the places menu (the places menu lists all the internal and external drives apart from the Linux ones - Main Filesystem and Swap). However exploring Filesystem through the Computer in Nautilus does indeed show a Home folder.

If you are asking because "locate lost+found" did not find a lost+found in home, I think that's because it finds the lost+found for every partition. I do not have a SEPARATE partition for /home or /boot. I'm assuming you probably do.

---

### Post by Andy06 on 2009-01-05
The following command:

```
sudo fdisk -l
```

gives this output:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a661e72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4735    38030088    7  HPFS/NTFS
/dev/sda2           14033       14593     4506232+   7  HPFS/NTFS
/dev/sda3            7493       14032    52532550    7  HPFS/NTFS
/dev/sda4            4736        7492    22145602+   5  Extended
/dev/sda5            4736        4801      530113+  83  Linux
/dev/sda6            4802        7374    20667591   83  Linux
/dev/sda7            7375        7492      947803+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Thanks cog. This shows for sure that it was created and is managed by Linux. sda5 is the offending partition. So it was not created by windows to identify or manage the logical partitions within the extended partitions

Unfortunately I am no closer to finding out why this is created and what it actually contains. And also why its size is variable from 20 MB to 700 MB. Everyone of the 16 computers I installed Ubuntu on has this partition.
I've stopped making further installs till I can find out what this is and how do I prevent it from occuring.

Thanks

---

### Post by The Cog on 2009-01-06
**sudo blkid** will tell you what the filesystem is. And **cat /etc/fstab** will tell you if it's normally mounted into your system. I don't think I've allowed the installer to automatically create partitions for years (I always manually partition to create a separate home partition) so I don't know if it's normal.

---

### Post by Andy06 on 2009-01-19
Ok I've been reading a little bit more about this and a lot of my friends have also been breaking our heads over it and we're pretty sure this mystery partition is an EBR or extended boot record/Extended Partition Boot Record.

The reason it has appeared in all the installation I've done is probably because all installation have been on extended partitions with the linux partitions being logical partition within the extended partition.

I suppose this will be increasingly common with all laptop manufacturers putting in a recovery partition. Combine that with the Windows and Data partitions and pretty much all dual boot notebook installs will be on extended partitions.

Thanks anyway for the help everybody!

---

