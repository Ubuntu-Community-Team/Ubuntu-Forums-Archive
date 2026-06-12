---
title: "Help with disk space management"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by greenjeddak on 2009-12-10
Hi, All:

First, I am a Windows convert of only a few days, so I don't know anything about Ubuntu and Linux.

Anyway, I have an Eee PC 900 with a 4 GB primary drive, on which I've installed Koala, and a 16 GB secondary drive.

I've noticed that I only have about 250 megabytes left of space on my drive, if you don't count the swap space (is that correct?). I think I've pretty much installed all the programs I want.

Is there any way to move my user account (is that the home account?) to the secondary drive, so that if I download things, or create new documents, etc., they don't eat up the small amount of space I have left? Or is that plenty of space when using a linux system?

Thanks so much.

---

### Post by jbrown96 on 2009-12-10
You're right swap doesn't count towards free space. It's like "emergency" ram; if you run out of actual ram, then Ubuntu will use the disk. It keeps the system from crashing, but is much slower than ram. 

You can certainly move your home folder. What's on the 16GB drive now? Is there a file system on it? In a terminal (apps-->accessories) please post the output of ```
cat /etc/fstab
``` and ```
sudo fdisk -l
```

---

### Post by greenjeddak on 2009-12-10
Hi, thank you for replying ...

I'm not at that system right now, but I will run those commands when I get home later. I'll post the output here afterward.

---

### Post by cariboo on 2009-12-10
I would suggest you open an Apllications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

The above command will remove archived packages from /var/cache/apt/archives. Depending on how many updates you have done, and how many extra programs you have installed, it should free up about 500Mb of space.

---

### Post by jbrown96 on 2009-12-10
> **cariboo907 said:**
> I would suggest you open an Apllications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

The above command will remove archived packages from /var/cache/apt/archives. Depending on how many updates you have done, and how many extra programs you have installed, it should free up about 500Mb of space.

This is a good command to run every few weeks, but I doubt that's the problem. Greenjeddak just installed the system a few days ago; the cache won't be very large.

---

### Post by greenjeddak on 2009-12-10
Thanks for the suggestion. I will run the clean command first, then run the other two commands. At the very least it will provide a more accurate report when I run the other commands.

---

### Post by jbrown96 on 2009-12-10
> **greenjeddak said:**
> Thanks for the suggestion. I will run the clean command first, then run the other two commands. At the very least it will provide a more accurate report when I run the other commands.

If you go to Apps-->Accessories there is a disk usage utitlty that can scan your hard drive and show you a nice pie chart on what's using that space.

---

### Post by freesitebuilder on 2009-12-10
I used this page to move my /home partition to give more space
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Lots of other stuff that I found really useful when I first started using Ubuntu.

---

### Post by t0p on 2009-12-10
> **freesitebuilder said:**
> I used this page to move my /home partition to give more space
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


This is what I would advise.  I also have an EeePC with a 4GB SSD, and also a 4GB SD card that I have permanently mounted in the SD card reader.  I installed Ubuntu so my /home directory is on the SD card.  That way I have not run out of space on the SSD.

---

### Post by greenjeddak on 2009-12-10
Hi, here are the outputs:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=38277bb4-3b3d-434e-975e-bc6678a236b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8218fa59-d01a-4ebe-bbc0-7143b2a7067c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

And:

```
Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04140414

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         461     3702951   83  Linux
/dev/sda2             462         490      232942+   5  Extended
/dev/sda5             462         490      232911   82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ec18ec1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1961    15751701    7  HPFS/NTFS

Disk /dev/sdc: 16.4 GB, 16437477376 bytes
255 heads, 63 sectors/track, 1998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4fa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1999    16048128    c  W95 FAT32 (LBA)

```

I'll look through the other references provided above. Thanks!

---

### Post by jbrown96 on 2009-12-10
/dev/sdc1 is your 16GB partition. 
1) Get any data on /dev/sdc1 off of it. Everything on there will be deleted, so make a backup. 

2) Create a proper linux filesystem on it. DO STEP #1 FIRST!!!! ```
sudo mkfs.ext4 -L Home /dev/sdc1
``` This will create an ext4 partition at /dev/sdc1

3) Determine the UUID of /dev/sdc1. This is a trial and error process, so you may have to repeat this several times. First create a mount point; you only need to create this once, no matter how many UUIDs you have to try. ```
sudo mkdir /media/new
```
4) Get a list of your UUIDs. ```
ls /dev/disk/by-uuid
``` Here's what I get for reference > 4899ec0f-7b97-43cd-8d93-688e1a1d8ade
72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3

5) We need to mount them one at a time and check the contents ```
sudo mount /dev/disk-by-uuid/UUID /media/new
``` replace UUID from with an entry from #4. If you type a few characters from, then you can press "tab" and it will autocomplete.
6) Check the directory and free space. ```
sudo ls /media/new && sudo df -h /media/new
``` The first part should list a single directory called "Lost+Found" and the second should report something close to 16GB. If it does, then you have found your UUID, and skip to step #8. Be sure to remember (or copy) the correct UUID.
7) unmount the partition ```
sudo umount /media/new
``` and go back to step #4. Choose the next UUID and re peat until you find it.
8 ) Copy your home folder to /media/new. ```
sudo cp -R /home/$USER/ /media/new && sudo chown -R $USER:$USER /media/new
``` The cp command might take a long time, depending on how much data you have.

9) Now we need to update your /etc/fstab. First, make a backup ```
sudo cp /etc/fstab /etc/fstab.back
```You need that UUID that we found earlier. ```
sudo gedit /etc/fstab
``` This will open a text editor. Find this line: > UUID=38277bb4-3b3d-434e-975e-bc6678a236b1 /               ext4    errors=remount-ro 0       1
 You want to copy and paste it at the end of the file. Then, change the UUID to what we found earlier and change / to /home Then save and exit the editor. 

10) The only thing left to do is destroy your old /home. This is kind of tricky, so I'm going to describe the easy way, but it may fail.

A) Try to delete your /home folder. This may fail because you are currently using it. First, check and make sure that /media/new/ has your user folder and everything is in it. If everything is in order, then do the following: Log out and switch to a virtual terminal (Ctrl+Alt+F2). Login at the text prompt, then run ```
sudo rm -rf /home
``` Hopefully there are no errors. If there weren't then, you should be able to mount the directory and enjoy the extra space. ```
sudo mount -a
``` If there were no errors, then logout ```
exit
``` and switch back to graphical mode (Ctrl+Alt+F7). Login and everything should be fine.

B ) If A failed, then you need to boot your Ubuntu CD or flash drive. Open a terminal and run, ```
sudo mkdir /media/old && sudo mount /dev/sda1 /media/old && sudo rm -rf /media/old/home
``` After that reboot and everything should be fine.

Cleanup:
If you got the 16GB partition mounted as your new /home, then we can do some cleanup. 
1) delete your backup fstab and the temporary mount point we used ```
sudo umount /media/new || sudo rm /etc/fstab.back && sudo rm -rf /media/new
```

---

### Post by jmate24 on 2009-12-11
> **jbrown96 said:**
> /dev/sdc1 is your 16GB partition. 
1) Get any data on /dev/sdc1 off of it. Everything on there will be deleted, so make a backup. 

2) Create a proper linux filesystem on it. DO STEP #1 FIRST!!!! ```
sudo mkfs.ext4 -L Home /dev/sdc1
``` This will create an ext4 partition at /dev/sdc1

3) Determine the UUID of /dev/sdc1. This is a trial and error process, so you may have to repeat this several times. First create a mount point; you only need to create this once, no matter how many UUIDs you have to try. ```
sudo mkdir /media/new
```
4) Get a list of your UUIDs. ```
ls /dev/disk/by-uuid
``` Here's what I get for reference 
5) We need to mount them one at a time and check the contents ```
sudo mount /dev/disk-by-uuid/UUID /media/new
``` replace UUID from with an entry from #4. If you type a few characters from, then you can press "tab" and it will autocomplete.
6) Check the directory and free space. ```
sudo ls /media/new && sudo df -h /media/new
``` The first part should list a single directory called "Lost+Found" and the second should report something close to 16GB. If it does, then you have found your UUID, and skip to step #8. Be sure to remember (or copy) the correct UUID.
7) unmount the partition ```
sudo umount /media/new
``` and go back to step #4. Choose the next UUID and re peat until you find it.
8 ) Copy your home folder to /media/new. ```
sudo cp -R /home/$USER/ /media/new && sudo chown -R $USER:$USER /media/new
``` The cp command might take a long time, depending on how much data you have.

9) Now we need to update your /etc/fstab. First, make a backup ```
sudo cp /etc/fstab /etc/fstab.back
```You need that UUID that we found earlier. ```
sudo gedit /etc/fstab
``` This will open a text editor. Find this line:  You want to copy and paste it at the end of the file. Then, change the UUID to what we found earlier and change / to /home Then save and exit the editor. 

10) The only thing left to do is destroy your old /home. This is kind of tricky, so I'm going to describe the easy way, but it may fail.

A) Try to delete your /home folder. This may fail because you are currently using it. First, check and make sure that /media/new/ has your user folder and everything is in it. If everything is in order, then do the following: Log out and switch to a virtual terminal (Ctrl+Alt+F2). Login at the text prompt, then run ```
sudo rm -rf /home
``` Hopefully there are no errors. If there weren't then, you should be able to mount the directory and enjoy the extra space. ```
sudo mount -a
``` If there were no errors, then logout ```
exit
``` and switch back to graphical mode (Ctrl+Alt+F7). Login and everything should be fine.

B ) If A failed, then you need to boot your Ubuntu CD or flash drive. Open a terminal and run, ```
sudo mkdir /media/old && sudo mount /dev/sda1 /media/old && sudo rm -rf /media/old/home
``` After that reboot and everything should be fine.

Cleanup:
If you got the 16GB partition mounted as your new /home, then we can do some cleanup. 
1) delete your backup fstab and the temporary mount point we used ```
sudo umount /media/new || sudo rm /etc/fstab.back && sudo rm -rf /media/new
```

This is too much work....
It would be great if you have an external drive to copy your data to ~160Gb should do.
Plus I would suggest after you have backed up your drives, when you go to reinstall ubuntu (xubuntu would be better) to use gparted to delete and resize your disks for the install. then load the installer (by double-clicking on the Install icon) and when you get to the setting up for you disks, choose manual and specify what partitions are for your / and /home partitions. (but remember that the / partition has to be formatted again) Secondly make sure you choose the same file system for both disks otherwise one or both disks may not be accessible.

jmate24 -- :)

---

