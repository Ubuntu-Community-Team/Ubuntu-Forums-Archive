---
title: "Slow/stalled boot up?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by natman on 2009-05-17
Hi,
I have noticed something that i thing is kinda odd with my boot up. After i pick Kubuntu on grub a line of text comes up,
"booting from (hda0,ext3) .... big string of digits"
This stays for about 10-15sec with no noise from the computer at all. Then the hard drive makes a noise ( not a bad one ) then Kubuntu graphic loader comes up and everything is fine.
My question is whats with that 10-15 sec delay does everyone have that?

Last point on shut down, i get the message "unable to itterate IDE..." "will now halt" whats that about?

Thanks:
Patrick

---

### Post by mapes12 on 2009-05-17
Some additional questions:

1. Has the machine being doing this ever since you installed UBU or is it a recent fault?
2. Is your configuration dual boot and if so which other OS(s)?
3. How did you setup your partitions to install UBU?

BTW - no, the error you have is not normal.

---

### Post by natman on 2009-05-17
Yes its being doing this since i did an install of 9.04
Yes its dual boot with Vista.
My set up is ext3 ( i opted for manual partitions ), i think 12Gb for \ and 130+ for \home ( they might not be exactly right numbers ) i have the copy of sudo fdisk -l below
> natman@natman-laptop:~$ sudo fdisk -l
[sudo] password for natman:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bcb0fb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19628   156122112    7  HPFS/NTFS
/dev/sda3           19629       20920    10377990   83  Linux
/dev/sda4           20921       38913   144528772+   5  Extended
/dev/sda5           20921       21163     1951866   82  Linux swap / Solaris
/dev/sda6           21164       38913   142576843+  83  Linux
natman@natman-laptop:~$



Just after reading it, does not end on cylinder boundary mean anything?

---

### Post by mapes12 on 2009-05-17
I think this is the problem > Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 27 Unknown
Partition 1 does not end on cylinder boundary. My fdisk output looks like this > mark@ubuntu-laptop:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x663c5122

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1033     8297541   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda3            1034        2325    10377990   83  Linux
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris

Partition table entries are not in disk order
mark@ubuntu-laptop:~$ but not sure how to fix your problem. My machine does not have Windoze, only Ubu.

---

### Post by natman on 2009-05-17
Okay thanks anyway, i just hope its not doing any harm to my machine. I will try posting again some other time perhaps someone else will know a solution.

Thanks:
Patrick

---

### Post by Aaardwark on 2009-05-17
Don't give up yet. I've found a few more with this problem. Most of them had resized a windows partition. I don't know if the problem is serious yet. Some people say this wont matter on modern systems, some say it's [bad]("http://www.linuxquestions.org/questions/linux-newbie-8/partition-1-does-not-end-on-cylinder-boundary-282563/"):

"That was not just a warning, this kind of thing is very dangerous:
/dev/hdc11 3892 4622 5859472+ 83 Linux
/dev/hdc12 4622 5351 5859472+ 83 Linux

The next partition starts at the same point where the previous ends, which can lead to data corruption if some bytes are written to the wrong partition.

If it was me, and especially concerning a server, I would doublecheck fdisk -l to see that the problem is gone."

---

### Post by Aaardwark on 2009-05-17
Found some more [info]("http://ubuntuforums.org/showthread.php?t=1070547"):

"Fortunately you don't need to worry at all about the "partition does not end on a cylinder boundary" type warning. "Cylinder" is mostly relevant to the ancient times when HDDs were less than 8.4 GB, and drives were accessed using the CHS geometry (Cylinders/Heads/Sectors) of the drive. Now that HDDs have outgrown the 8.4 GB limit of CHS notation, all modern HDDs use "LBA" (Logical Block Addressing) in order to access the data on the HDD, rather than the CHS method; LBA notation is limited to a max drive size of 2 TB, so it is far more suitable for modern drives, although even it is now becoming dated. But since the standard MS-DOS MBR (Master Boot Record) partition table hasn't changed since those times, partition editors still have to "fill in the blanks" for the CHS notation that is included in the partition table. Since CHS geometry has no physical relevance to modern drives, that means that it is entirely arbitrary which CHS geometry the partition editor assumes when it sets up the partitions. And it just so happens that most Windows partition editors assume a different geometry than the standard that Linux uses, i.e. 255 Heads, 63 sectors/track geometry. So bottom line, often Linux will report "partition does not end on a cylinder boundary" warnings when reading the partition table of drives that were partitioned with Windows software, but that's entirely OK and nothing to be concerned about."

It seems to be nothing to worry about. It is due to how discs were partitioned ages ago, and how windows does it now. You can do something about it if you dislike the error message, and extra boot time.

---

### Post by natman on 2009-05-17
Wow Thanks very much for all the info, any chance you would know how to actually "fix" the problem. Now harm to learn these things!

---

### Post by Aaardwark on 2009-05-17
The halt message seems to be [one]("https://bugs.launchpad.net/ubuntu/+bug/193125") ef [two]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298402") bugs.

For one there seems to be a workaround. If you computer still shuts down by itself when told to, I'd ignore it or help with the bug reporting.

---

### Post by Aaardwark on 2009-05-17
The solutions I've found regarding the cylinder boundary thing, is reformatting or resizing partitions. Reformatting seems a bit extreme for eliminating an error message. :) Resizing the windows partition wouldn't be to bad, unless you've filled your entire windows partition.

My recommendation for doing so would be:
-Defragment in windows (This will place all the files in the beginning of the partition.)
-Backup valuable data (It's good to do anyways, and always good when messing with partitions.)
-Burn a live-cd of Ubuntu (If you don't already have one.)
-Boot live-cd, and start gparted
-Choose to resize the ntfs partition, and remove the few megabytes to round it off nicely.

---

