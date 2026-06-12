---
title: "Can't find C drive"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by poc52ks on 2010-11-22
Ok so I'm new to ubuntu and tried it out for a week before i tried to dual boot my system with windows 7/ubuntu 10.10. After the installation there was no prompt for me to choose which OS to boot into. I figured i messed up and wrote over my partition, but when i log in and go to places all i have is file system. I can't find my c drive. I know this is a total noob thing but i would just like to know if my c drive is completly gone forever or should i try and reinstall ubuntu.

---

### Post by muteXe on 2010-11-22
open a terminal and type:
```

sudo fdisk -l

```

and paste output in here please mate. (that's a small L, not a 'one').

---

### Post by elliotn on 2010-11-22
there wont be c drive in ubuntu but on places you will see  the partitions in sizes

---

### Post by poc52ks on 2010-11-22
I get off in a few hours and will paste my results. When i was running from the cd i know it didn't say C drive exactly but there was some sort of partition there, but now the only thing there is just the filesystem.

---

### Post by muteXe on 2010-11-22
That command i posted will at least tell you if you're windows partition is still there or not. Would be a good place to start :)

---

### Post by poc52ks on 2010-11-22
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000003ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37384   300281856   83  Linux
/dev/sda2           37384       38914    12286977    5  Extended
/dev/sda5           37384       38914    12286976   82  Linux swap / Solaris

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021968

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60716   487699456    7  HPFS/NTFS

---

### Post by surfer on 2010-11-22
> **poc52ks said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60716   487699456    7  HPFS/NTFS

this seems to be your 'C drive'. you can mount it with
```
$ sudo mount -t ntfs /dev/sdb1 /mnt
```
and then browse /mnt.

---

### Post by poc52ks on 2010-11-22
when i attempt to mount it says 

Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

It is not in my places though. When i open up computer the only thing in there is my dvd drive and file systems.

---

### Post by poc52ks on 2010-11-22
I realized my external HDD was plugged in and when i reran the terminal i got this

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000003ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37384   300281856   83  Linux
/dev/sda2           37384       38914    12286977    5  Extended
/dev/sda5           37384       38914    12286976   82  Linux swap / Solaris

---

### Post by Old_Grey_Wolf on 2010-11-22
If your external drive was only for storage then yes your Windows partition was overwritten.

---

### Post by poc52ks on 2010-11-22
Ok i figured my windows partition was gone so i did a clean reinstallation of ubuntu in hopes that this would fix my problem. i still only have file manager when i open computer. i know my partition is not called C: but how do i get access to my main partition.

---

### Post by Old_Grey_Wolf on 2010-11-22
When you use the menu Places > Computer, the icon labeled "File System" is what Windows would call your C: drive. On your Linux system it is sda1. If you open that icon by double-clicking you will see a folder called "home". If you double-click that icon you will see a folder with your user name. If you double-click that icon you will see a Documents folder, Music folder, Pictures folder, etc.

---

### Post by mike555 on 2010-11-22
looks to me like you have overwritten your Windows system (twice)

---

### Post by Old_Grey_Wolf on 2010-11-22
If you have anything on your external HDD you would like to copy to your Documents, Music, Pictures folders, you can use a forced mount. When you overwrote Windows the external HDD had not been safely disconnected so the HDD thinks that Windows is still using it. That is why you got the error "Mount is denied because the NTFS volume is already exclusively opened." You can still mount it by using the following commands

```
sudo mkdir /media/external
sudo ntfs-3g /dev/sdb1 /media/external -o force
```

Edit: before you shut down the computer or disconnect the external drive be sure to unmount it with this command

```
sudo umount /media/external
```

---

### Post by Old_Grey_Wolf on 2010-11-22
> **mike555 said:**
> looks to me like you have overwritten your Windows system (twice)

Yes, he or she has, and the second time knowingly. The Ubuntu 10.10 installer is not as intuitive as previous installers. Even experienced users have overwritten their other partitions when using it. Since he or she hasn't posted "OMG how do I get my files back?", I think the external HDD may include a backup of important files.

---

### Post by angelgz123 on 2013-03-13
You can access your Windows files by navigating 

Goto  <File System> 

Then goto <Host>

walla you see your C drive folders.

---

### Post by nothingspecial on 2013-03-13
Old thread.

Closed

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

