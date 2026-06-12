---
title: "Accessing Windows Partition in which Ubuntu is installed"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Anant on 2009-04-02
Hi everyone,

I am very much new to Ubuntu and already fascinated by the OS and what it has in store for everyone. 

I have Windows XP in my laptop. It has two partitions (c: and d: ). I have installed Ubuntu 8.10 in "D:" partition. Everything went well during and after installation and I am enjoying using it. Just have a problem, when I boot into Ubuntu "C:" partition of Windows is auto mounted and I am able to access the partition and read/write files. But I am not able to see "D:" the partition in which Ubuntu is installed.
Unfortunately all my data in "D:" and I am unable to access it when I am in Ubuntu.

Please help!

-Anant

---

### Post by PacSci on 2009-04-02
Open a terminal, and run the command "sudo fdisk -lu". It should output a list of partitions similar to this:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1030102f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   509613929   254806933+  83  Linux
/dev/sda2       509613930   515397329     2891700   82  Linux swap / Solaris
/dev/sda3       515397330   976768064   230685367+  83  Linux

```

Of course, yours might have more disks, and WILL have different partitions. Next, run "df" and it will return something like:

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            228868144  12246612 205087268   6% /
tmpfs                   906356         0    906356   0% /lib/init/rw
varrun                  906356       236    906120   1% /var/run
varlock                 906356         0    906356   0% /var/lock
udev                    906356      2760    903596   1% /dev
tmpfs                   906356      1504    904852   1% /dev/shm
lrm                     906356      2004    904352   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1            250806992    748720 237317928   1% /stor

```

The first column in "df" corresponds to the first column in "fdisk -lu". If you post those outputs here, someone will be able to help you from there.

---

### Post by elliotn on 2009-04-02
U cannot se the d: partition coz windows cant read ext3 file system but u can read the windows partition as ubuntu can read ntfs, search google for some app that help windows read ext3 file system

---

### Post by tarps87 on 2009-04-02
> **Anant said:**
> Hi everyone,

I am very much new to Ubuntu and already fascinated by the OS and what it has in store for everyone. 

I have Windows XP in my laptop. It has two partitions (c: and d: ). I have installed Ubuntu 8.10 in "D:" partition. Everything went well during and after installation and I am enjoying using it. Just have a problem, when I boot into Ubuntu "C:" partition of Windows is auto mounted and I am able to access the partition and read/write files. But I am not able to see "D:" the partition in which Ubuntu is installed.
Unfortunately all my data in "D:" and I am unable to access it when I am in Ubuntu.

Please help!

-Anant

How did you install Ubuntu, through windows (wubi) or from the live cd?
Are you saying that you're data was on the 'd:' drive before the install or can you still access it from windows?

Can you also follow PacSci's post.

---

### Post by elliotn on 2009-04-02
I think he want to say the data is in windows if he installed windows first but if he installed ubuntu first the the data is in the ext3 thus he cant access it when in windows.

---

