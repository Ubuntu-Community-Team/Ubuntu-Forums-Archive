---
title: "nput/output error during write on /dev/sda ubuntu unable to install"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Akaash on 2009-10-08
**"input/output error during write on /dev/sda ubuntu unable to install**"

Hi there I'm fairly new to Ubuntu, I've tried to install 9.04 on my computer but it gives me the error that I posted up top there.  I did a memtest with no errors, and I did the system defect check (both from the live CD).  In both cases there were no problems.  I can access Ubuntu from the CD but am unable to install it.  When I go to the partition manager there is nothing selectable.  I was wondering what might be a good idea to try next as I am kind of lost. 

Thank you very much,

Akaash

---

### Post by LowSky on 2009-10-08
does you computer have a  hard drive, and if yes, is it installed properly? Does BIOS recognize it?

---

### Post by jbrown96 on 2009-10-08
Is there any data on the disk that needs to be saved or are you going to use the entire drive for Ubuntu? 
We can get a better idea of what is happening with your system if you post the output of ```
sudo fdisk -l
```

---

### Post by Akaash on 2009-10-08
Sorry, but how do I check to see if BIOS recognizes my hard drive?

And no, nothing needs to be saved, I cleared everything though, I don't even have an OS on it right now

Ok I'll try that "sudo fdisk -1"

---

### Post by Akaash on 2009-10-08
so this is what I get with fdisk:

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ 


Any thoughts?

---

### Post by jbrown96 on 2009-10-09
that's a lowercase L, not a number one.

---

### Post by Akaash on 2009-10-13
so I copied and pasted "sudo fdisk -l" and it doesn't give me an output

---

### Post by Akaash on 2009-10-13
ok so I restarted my computer and now the command worked for some reason... anyways I'm showing it below

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x783dd97e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23573   189350091   83  Linux
/dev/sda2           23574       24321     6008310    5  Extended
/dev/sda5           23574       24321     6008278+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
 
haha, this doesn't mean much to me, does anyone have thoughts on this?

---

