---
title: "filesystem mount failed"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-02-13
I am using Kubuntu 10.04  and suddenly yesterday there was booting problem and i got this error message. Waiting for some to rescue my os. 

thank



**Init : plymouth main process (304) killed by BUS signal**
  **exec: 14 : mountall : Input/output Error**
  **init : mountall main process (323) terminated with status 2**
  **init : Failed to spawn console-setup main process : unable to execute : Input/output error**
  **init : plymouth-stop pre-start process (327)  terminated with status 2**
  **Filesystem check or mount failed.**
  **A maintenance shell will now be started.**
  **CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored.**
  **/proc/self/fd/8 : 20 : /sbin/sulogin : Inpuy/output error**
  **init : mountall-shell main process (328 ) terminated with status 2**
  **exec : 10 : start : Input/output error**
  **init : mountall-shell post-stop process (330) terminated with status 2**

---

### Post by 1991sudarshan on 2011-02-13
????

---

### Post by aaryansh on 2011-02-13
I can only think of 2 reasons why this would happen.
1> something wrong with the filesystem,
try to fsck.

2> something wrong with fstab,
may help if you post your fstab.

---

### Post by vanadium on 2011-02-13
Indeed I can only second this. However, in the absolute beginners section, you might want/need more specific instructions.

* Checking your partitions

Probably you'd best boot from a live CD for this. Open a terminal

Issue the command "sudo blkid" (no password needed in a live session, I believe) to see all your partitions. Each line starts with a device name denoting your partition, e.g. /dev/sda1.

Issue the command "mount" to see if any partition is mounted. Again, the lines for partitions will start with the device name. If any is mounted, unmount it:

```

sudo umount /dev/sda1

```

where you replace the /dev/sda1 part by the actual device name.

Then check your partitions:

```

sudo fsck /dev/sda1

```
again replacing the /dev/sda1 part by the actual device name of the partition you want to check.

* Checking your /etc/fstab.

I am not quite sure anything could have gone wrong here, except if you have played around with /etc/fstab. If all your partitions prove to be healthy (previous section), then indeed you will need to check the contents of the file fstab on your boot partition.

---

### Post by 1991sudarshan on 2011-02-15
> **vanadium said:**
> Indeed I can only second this. However, in the absolute beginners section, you might want/need more specific instructions.

* Checking your partitions

Probably you'd best boot from a live CD for this. Open a terminal

Issue the command "sudo blkid" (no password needed in a live session, I believe) to see all your partitions. Each line starts with a device name denoting your partition, e.g. /dev/sda1.

Issue the command "mount" to see if any partition is mounted. Again, the lines for partitions will start with the device name. If any is mounted, unmount it:

```

sudo umount /dev/sda1

```where you replace the /dev/sda1 part by the actual device name.

Then check your partitions:

```

sudo fsck /dev/sda1

```again replacing the /dev/sda1 part by the actual device name of the partition you want to check.

* Checking your /etc/fstab.

I am not quite sure anything could have gone wrong here, except if you have played around with /etc/fstab. If all your partitions prove to be healthy (previous section), then indeed you will need to check the contents of the file fstab on your boot partition.


I have executed the commands which you asked me to do in the live session 

[B]ubuntu@ubuntu:~$ sudo blkid
  /dev/loop0: TYPE="squashfs" 
  /dev/sda1: UUID="2C29852E5882DF9E" TYPE="ntfs" 
  /dev/sda3: UUID="C4ECBF75ECBF5FFA" TYPE="ntfs" 
  /dev/sda5: UUID="287fbd4d-409f-4919-ae02-003c5592f0fd" TYPE="ext4" 
  /dev/sda6: LABEL="MINE" UUID="78A0AAFCA0AAC04C" TYPE="ntfs" 
  /dev/sda7: UUID="118ABCE91B5647ED" TYPE="ntfs" 
  /dev/sda8: UUID="A8F413FDF413CC86" TYPE="ntfs" 
  /dev/sdb1: UUID="AA77-0734" TYPE="vfat" 





[/B]     [B]   
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
  fsck from util-linux-ng 2.17.2
  e2fsck 1.41.12 (17-May-2010)
  /dev/sda5 has been mounted 224 times without being checked, check forced.
  Pass 1: Checking inodes, blocks, and sizes
  Pass 2: Checking directory structure
  Error reading block 532807 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
   
  Force rewrite<y>? yes
   
  Error reading block 534851 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
   
  Force rewrite<y>? yes
   
  Error reading block 535798 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
   
  Force rewrite<y>? yes
   
  Error reading block 1056865 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
   
  Force rewrite<y>? yes
   
  Error reading block 1056866 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
                                                                                                                                                                                                  
  Force rewrite<y>? no                                                                                                                                                                            
                                                                                                                                                                                                  
  Error reading block 1056867 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes                                                 
                                                                                                                                                                                                  
  Force rewrite<y>? yes                                                                                                                                                                           
                                                                                                                                                                                                  
  Error reading block 1581437 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
   
  Force rewrite<y>? yes
   
  Error reading block 1581438 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
   
  Force rewrite<y>? yes
   
  Error reading block 1581439 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
   
  Force rewrite<y>? yes
   
  Error reading block 1581440 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? no
   
  Error reading directory block 1581440 (inode 391824): Attempt to read block from filesystem resulted in short read
  Continue<y>? yes
   
  Error reading block 1581441 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes
   
  Force rewrite<y>? no
   
  Error reading block 1581442 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? no
   
  Error reading directory block 1581442 (inode 391824): Attempt to read block from filesystem resulted in short read
  Continue<y>? no
  e2fsck: aborted
    
[/B]

---

### Post by 1991sudarshan on 2011-02-15
Is there any other way to remove the error reading those blocks in the linux partition.????

---

### Post by vanadium on 2011-02-15
This looks like a severe problem with the file system. Could have been caused by a power outage on the wrong moment, or it might indicate a failing hard drive.

To me, it looks as if the only solution will be to reformat the file system, i.e. reinstall the operating system. If after reinstalling the error reappears quickly without a good reason (e.g. a power outage), then it will most likely be the drive that is failing.

---

### Post by 1991sudarshan on 2011-02-16
> **vanadium said:**
> This looks like a severe problem with the file system. Could have been caused by a power outage on the wrong moment, or it might indicate a failing hard drive.

To me, it looks as if the only solution will be to reformat the file system, i.e. reinstall the operating system. If after reinstalling the error reappears quickly without a good reason (e.g. a power outage), then it will most likely be the drive that is failing.

some times back i used ubuntu live cd to boot in in the notification area i got a message that "imminent disk failure". i never got such message while using kubuntu live cd. is there any other way to restore my os other than formating it??

---

### Post by vanadium on 2011-02-18
Not if you cannot rescue the file system with fsck.

---

### Post by inobe on 2011-02-18
i would use a live cd wile you have a chance to drag your wanted pics, music, docs, vids to a flash drive or dvd!

then after that, do

```
sudo fsck -f -p /dev/sda1
```

-f will force checking

-p will repair with no questions asked.

if that fails, your hard drive may need replacing, you can risk reinstalling to it, i seriously doubt you would get a month of operation from it.

if anything fails, at least you have your data backed up, it only takes a half hour to install ubuntu.

---

### Post by BiggieLounge on 2011-02-25
[FONT=&quot]Error reading block 24739840 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error<y>?[/FONT]

---

### Post by BiggieLounge on 2011-02-25
[FONT=&quot]pls help!!!!
tHIS IS THE ERROR I HAVE BEEN GETTING.
Error reading block 24739840 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error<y>?[/FONT]

---

