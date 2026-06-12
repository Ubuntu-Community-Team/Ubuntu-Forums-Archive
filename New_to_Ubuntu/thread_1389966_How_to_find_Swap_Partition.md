---
title: "How to find Swap Partition"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Civil_777 on 2010-01-25
Hi, I am a relative newbie here.  I recently installed Ubuntu Server 8.04 and I am trying to figure out if I have a swap partition correctly setup.  When I checked my partitions using "fdisk -l", I see the following:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        5005    39953655    5  Extended
/dev/sda5              32        5005    39953623+  8e  Linux LVM

It looks like I have no swap at all.  However, when I check my memory usage using "free", I see the following:

                total         used         free       shared    buffers     cached
Mem:        108320     105696       2624          0       1588      67060
-/+ buffers/cache:      37048      71272
Swap:       323576      20264     303312


This makes it look like the server is using some sort of swap.  Perhaps it is a swap file?  Does anyone know why my server appears to be using swap without a swap partition?  Thanks for the help!

---

### Post by tom4everitt on 2010-01-25
Try:

swapon -s 

That should list partions/files currently used as swap.

---

### Post by Civil_777 on 2010-01-25
Nevermind, I checked the fstab file and saw that there appears to be a swap file that is mounted at boot time.

---

### Post by Civil_777 on 2010-01-25
Nice suggestion for the swapon command!  I see the swap file there too.

---

