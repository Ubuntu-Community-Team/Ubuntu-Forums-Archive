---
title: "My 2 TB partition is lost without any reason :O"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by legolas_w on 2010-05-13
Hello everyone.

I have an external hard disk with a 2 TB ext3 partition. Now that I attach it to my computer is says that no partition exists. is there any way to recover the partition and fix the problem? 

I have lost 1.6 TB of music, photos, tv series,...

Thanks.

---

### Post by Sealbhach on 2010-05-13
Does it show up when you run lsusb?

Also, look at some of the threads where [people have had similar issues]("http://www.google.co.uk/#hl=en&safe=off&q=ubuntuforums+external+hard+drive+not+detected&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=5bc7b921c75de95b"), and try some of the solutions that were found to work.

.

---

### Post by srs5694 on 2010-05-13
Show the output of "sudo fdisk -lu" when typed at a command prompt. Please enclose the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string. I may ask for additional diagnostic information. *Do not* do anything potentially destructive (such as running the testdisk program) until you know the cause of the problem.

---

### Post by legolas_w on 2010-05-13
Hello everyone,

I will not run any intrusive command on the disk. The disk contains 10 years of my life.

```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29f418d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    43600409    21800173+  83  Linux
/dev/sda2        43600410   156248189    56323890   83  Linux
/dev/sda3       156248251   242179874    42965812    5  Extended
/dev/sda4       242179875   312576704    35198415   83  Linux
/dev/sda5       156248253   234372284    39062016   83  Linux
/dev/sda6       234372348   242179874     3903763+  82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79ea3d1b

   Device Boot      Start         End      Blocks   Id  System


```

Thanks.

---

### Post by legolas_w on 2010-05-13
My data must be there but somehow the partition table or whatever the name is, has been lost.  

So there should be some way to recover the files, right?

Thanks.

---

### Post by Raiju on 2010-05-13
have you tried testdisk? is a partition recovery tool and its should find your data.

---

### Post by srs5694 on 2010-05-13
Don't try testdisk just yet; it could get it wrong and therefore make matters worse. It looks like the disk has no Master Boot Record (MBR) partitions defined. Do you know if the disk was partitioned using the MBR or the GUID Partition Table (GPT) system? If it was partitioned using GPT, its backup partition table might yet be intact. In that case, you could recover it, without guesswork, by using my [GPT fdisk](https://sourceforge.net/projects/gptfdisk/files/) (gdisk) program. See my [Repairing GPT Disks](http://nessus.rodsbooks.com/gdisk/repairing.html) Web page for some tips. Your disk is just under the boundary of being big enough to require GPT, though, so there's a good chance that it used MBR, and if it used MBR, this won't work. Still, there's no harm in firing up gdisk on the disk. If it can't find a trace of GPT data structures, you can always exit with 'q' and no harm will be done.

If this fails, then testdisk may be the best option. The alternative would be to try blindly creating partitions at certain likely locations. (If the disk had just one partition, then chances are it started at sector 63 or 2048; although if it was a GPT disk, 34 and 40 are also likely possibilities.) What testdisk does is to scan the disk for known filesystem data structures, so if they still exist, testdisk *should* be able to find them and recreate the partition; however, testdisk sometimes gets confused if the disk had ever been re-partitioned or if you'd ever created one filesystem over another one, hence my suggestion to use testdisk only once you've run out of non-destructive possibilities. I'd use testdisk before writing random or best-guess partition tables to the disk, though.

---

### Post by legolas_w on 2010-05-13
Thank you all for helping me on this. I was going to throw up when the disk failed. 

Now I have recovered the parition in less than 2 minutes using the TestDisk. The whole drive was one parition and I have only partitioned the drive once. TestDisk just found the partition and recovered it.

Thank you all for your help.

---

### Post by srs5694 on 2010-05-13
You may want to back up your partition tables (for both your disks) as insurance should this happen again. The "Final Conversion Thoughts" section of [this Web page](http://www.rodsbooks.com/gdisk/mbr2gpt.html) of mine provides instructions on how to do this.

---

