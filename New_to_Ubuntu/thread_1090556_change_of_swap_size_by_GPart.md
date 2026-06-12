---
title: "change of swap size by GPart"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by t.choi on 2009-03-08
Hi,

I have used Gpart to change my swap partition size after then it can not be auto-active. I need active the swap every time after re-boot.

Thank you for helping

Thomas Choi

---

### Post by taurus on 2009-03-08
When you resized swap, the UUID for swap partition would change so you need to change the old UUID in /etc/fstab for swap with the new one.

```
sudo blkid
```

---

### Post by t.choi on 2009-03-08
It does not work, the swap still not active after re-boot.

---

### Post by taurus on 2009-03-08
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free -m
```

---

### Post by kansasnoob on 2009-03-08
You probably lost your quiet Usplash also.

Go to terminal and run:

```
sudo blkid -c /dev/null
```

That will display something like this:

> /dev/sda1: UUID="5A3CAE183CADEEE7" TYPE="ntfs"
    /dev/sda5: UUID="3f6a93da-cbc0-4203-92ce-42ff70394f0a" TYPE="ext3"
    /dev/sda6: TYPE="swap" UUID="5b397135-2a82-4933-aefd-00d7ff23b413"
    /dev/sda7: UUID="cb8d8925-8059-46bc-8312-9ce5f42afa91" SEC_TYPE="ext2" TYPE="ext3" 

Note: The UUID #'s are in parenthesis. DO NOT include the parenthesis when you replace the UUID's in the following files! BTW the "-c /dev/null" is necessary because if you run blkid without options it reads from its cache file. If you've run it before and any partition has changed you'll get erroneous results.

Now run:

```
cat /etc/fstab
```

You'll undoubtedly see that the UUID's for SWAP are different. Here I like to create a simple backup of the original /etc/fstab using copy-n-paste and either Abiword or Open Office so if I hose things I can put things back in their original state! Do NOT be concerned at this point if the partition #'s are different! DO NOT change a partition #! Change nothing but UUID's!

To edit that file run:

```
gksudo gedit /etc/fstab
```

It's much, much easier to cut- copy-n-paste! Just be careful! And when you're done editing remember to click on Save, then go to File > Quit!

Now on to /etc/initramfs! Run:

```
cat  /etc/initramfs-tools/conf.d/resume
```

That UUID should (but won't) match the UUID for SWAP in blkid so to edit:

```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

Again be sure to save > file > quit after editing! Now one last important thing:

In terminal:

```
sudo update-initramfs -u
```

Be patient! It takes a minute or two to run! Wait until the command prompt (like lance@lance-desktop) shows up again!

Clear as mud?

---

### Post by t.choi on 2009-03-09
Dear taurus

Thank you for your help

following your code typied on terminal as shown below 



thomas@linux-ubuntu:~$ sudo fdisk -l 
[sudo] password for thomas: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x040d040c 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        5737    46082421   83  Linux 
/dev/sda2            5738       14593    71135820    5  Extended 
/dev/sda5           14078       14593     4144770   82  Linux swap / Solaris 
/dev/sda6           12912       13695     6297448+  83  Linux 
/dev/sda7           13696       14077     3068383+  82  Linux swap / Solaris 
/dev/sda8            5738       12670    55689259+  83  Linux 
/dev/sda9           12671       12911     1935801   82  Linux swap / Solaris 

Partition table entries are not in disk order 
thomas@linux-ubuntu:~$ cat /etc/fstab 
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sda8 
UUID=49ad58aa-d48d-47b8-87ca-ffb8bb67cd6d /               ext3    relatime,errors=remount-ro 0       1 
# /dev/sda9 
UUID=37754ab8-7e45-44b3-91f1-359b3be6080f none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
thomas@linux-ubuntu:~$ free -m 
             total       used       free     shared    buffers     cached 
Mem:           501        493          7          0         12        227 
-/+ buffers/cache:        253        247 
Swap:            0          0          0

 and it still not work

---

### Post by t.choi on 2009-03-09
Dear kansasnoob

Thank you ur help and the explanations

It function well and the swap auto-mounted after reboot it. 
The most of The codes I do not know just followed.


Thanks again !

---

### Post by TheGoblin on 2009-03-28
Be warned that changing the swap partition can also cause problems with hibernation, see my post at [http://ubuntuforums.org/showthread.php?t=1090318]("http://ubuntuforums.org/showthread.php?t=1090318").

---

