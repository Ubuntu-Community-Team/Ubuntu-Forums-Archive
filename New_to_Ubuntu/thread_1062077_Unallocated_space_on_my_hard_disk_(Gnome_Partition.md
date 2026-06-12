---
title: "Unallocated space on my hard disk (Gnome Partition Editor)"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by mysticanonymous on 2009-02-06
Hello, 
I am totally new to Linux and I have tried to get help with this problem before, but did not have the time to continue with steps that didn't help, to finally find the right one. I am currently trying to install ubuntu into an old IBM and well... my whole hard drive in unallocated space, and has no current operating system on it. I have made a new partition and tried to install to that and it will not work, any suggestions?

---

### Post by taurus on 2009-02-06
Just tell the installer to use the whole harddrive.  That is one option.  Another option is use gparted from the LiveCD (System -> Administration) and partition it yourself.  You need at least two partitons:  one for / (root filesystem) and one smaller one for swap.  However, it's good idea to also create a third one for /home.  Then, use the Manual option when you get to the partition screen and mount one partition to / and one to /home.

---

### Post by mysticanonymous on 2009-02-06
I have tried to do that with a new partition an it tells me that i has failed..

---

### Post by taurus on 2009-02-06
You mean using the whole harddrive option?

Open a terminal and post the output of this command from the LiveCD.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mysticanonymous on 2009-02-06
alrighty.. well I am not to familiar with Linux so what do I do from there... I dont really know programming.

---

### Post by taurus on 2009-02-06
There is no programming.  Just open a terminal and type in that command.  Then, post the whole output here.

---

### Post by avtolle on 2009-02-06
You have booted up the Live CD, correct? From the desktop that comes up in the Live CD, get to a terminal by clicking on Applications in the top panel; from the list that appears, select Accessories; then,  from that list, Terminal. When the terminal window opens, enter the command ```
sudo fidsk -l
```at the prompt. Then, copy the output from that command and post it here so it can be looked over by those trying to assist.

---

### Post by mysticanonymous on 2009-02-06
er ubuntu isnt letting me use the internet.. 
I am on here with my laptop..

---

### Post by mysticanonymous on 2009-02-06
finally.... 
here... 
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by taurus on 2009-02-06
That last letter is a lower case letter L, not number 1.

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```

---

### Post by jerome1232 on 2009-02-06
```
sudo fdisk -l
```

not
```
sudo fdisk -1
```

The number 1 and the letter l (L) do look pretty similar though ;)

---

### Post by mysticanonymous on 2009-02-06
alrighty...  mistook it for a one

---

### Post by mysticanonymous on 2009-02-06
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfffdfff

Disk /dev/sda doesn't contain a valid partition table
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-02-06
> **mysticanonymous said:**
> ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfffdfff

Disk /dev/sda doesn't contain a valid partition table
ubuntu@ubuntu:~$

From the LiveCD, use gparted (System -> Administration -> Partition Editor) and create a partition, /dev/sda1, that takes up the whole harddrive.  Then, format it to ext3 filesystem.  Close gparted window and click on the install icon on the desktop.  Tell the installer to use the whole harddrive when you get to the partition screen (I believe it's step 4 of 7).

---

### Post by mysticanonymous on 2009-02-06
Its no finished, but I think thta is going to work, OMG thank you ive been trying to do this for some time now...

---

