---
title: "Installing on partitioned HD"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Jasper7g on 2009-05-20
I am very new to Linux/Ubuntu and am just feeling my way. I have a second HD on my computer that is  in several partitions of about 17-gbytes. I think that is too small to install Ubuntu on. Am I correct? Secondly, if I try to install on one of the partitions (not within Windows) will it make room by moving the partitions, or do I have to get the HD cleared of the partitions?

---

### Post by iaculallad on 2009-05-20
> **Jasper7g said:**
> I am very new to Linux/Ubuntu and am just feeling my way. I have a second HD on my computer that is  in several partitions of about 17-gbytes. I think that is too small to install Ubuntu on. Am I correct? Secondly, if I try to install on one of the partitions (not within Windows) will it make room by moving the partitions, or do I have to get the HD cleared of the partitions?

Actually, 17GB is too much for Ubuntu to be installed. Base requirement is only 4GB.
You don't need to clear your HDD in order to install Ubuntu. You can make another partition within your 17GB partition for Ubuntu to use.

---

### Post by renkinjutsu on 2009-05-20
The installer will not automatically adjust your partition sizes, at install, you're given 3 options

-to install over the entire harddrive
-to install within largest contiguous space
-manual partitioning

fortunately for you, linux has a very small kernel and it is POSSIBLE to install ubuntu in a partition that's 4 or so gigabytes (I THINK) ... but 17GB is definitely enough for an ubuntu installation (you'll probably have a few gigabytes left to use for yourself)

when you're more comfortable with messing with your computer, you can always repartition your drives or even upgrade to a bigger harddrive, the people on this forum are generally very helpful

---

### Post by alphacrucis2 on 2009-05-20
> **Jasper7g said:**
> I am very new to Linux/Ubuntu and am just feeling my way. I have a second HD on my computer that is  in several partitions of about 17-gbytes. I think that is too small to install Ubuntu on. Am I correct? Secondly, if I try to install on one of the partitions (not within Windows) will it make room by moving the partitions, or do I have to get the HD cleared of the partitions?

The Live CD includes a program called gparted which is available under the menus as system -> administration -> partition editor. From that you can view the partitions on each disk, delete, create, resize partitions to your hearts content. The installer also has a manual option which allows you to partition things as you would like. Normally you would set up one large partition as ext3 (or the newer ext4 file system) and a small partition of about double your system RAM in size as type 'swap'. Some people like to split off the /home directory onto its' own partition (has some advantages if things go wrong). If you do that then say allocate say 15GB to the root filesystem (mountpoint / ) and allocate all the rest other than swap to the /home directory (mountpoint /home ).

---

### Post by Jasper7g on 2009-05-20
Thank you.

---

### Post by Jasper7g on 2009-05-20
> **alphacrucis2 said:**
> The Live CD includes a program called gparted which is available under the menus as system -> administration -> partition editor. From that you can view the partitions on each disk, delete, create, resize partitions to your hearts content. The installer also has a manual option which allows you to partition things as you would like. Normally you would set up one large partition as ext3 (or the newer ext4 file system) and a small partition of about double your system RAM in size as type 'swap'. Some people like to split off the /home directory onto its' own partition (has some advantages if things go wrong). If you do that then say allocate say 15GB to the root filesystem (mountpoint / ) and allocate all the rest other than swap to the /home directory (mountpoint /home ).
Pardon my ignorance but what do you mean by "Live CD"? Would that be the install CD on which I burned the download?

---

### Post by alphacrucis2 on 2009-05-20
> **Jasper7g said:**
> Pardon my ignorance but what do you mean by "Live CD"? Would that be the install CD on which I burned the download?

Yes. It is not only an install CD, You can also run Ubuntu from the CD to test that all your hardware works without actually installing anything. It is slow though as it is loading from programs from the CD rather than the hard disks.

---

