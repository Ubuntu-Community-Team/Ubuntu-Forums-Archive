---
title: "Cant Get to my XP files"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by koopa225 on 2009-01-10
hey im new to Ubuntu, and I had Windows XP installed first and I installed Ubuntu and I thought I was installing it alongside Windows, now I cant get Windows to boot up and I really need to get my music and pictures off of XP. Can somebody help me out and point me in the right direction for this please?

---

### Post by taurus on 2009-01-10
You can use ntfs-config to mount your windows partition first before you can access it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by ibizatunes on 2009-01-10
When you boot does it come up with a error? Can you post it...

---

### Post by ithanium on 2009-01-10
check this thread: [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

### Post by stanz on 2009-01-10
Installing along side of it? ...(or another 'partition')

Using the ntfs-config may be your easy way to go...
> **taurus said:**
> You can use ntfs-config to mount your windows partition first before you can access it.

Slow down and read all that comes at ya, during the install and all else!
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Things are different when ya step away from the m$ world.

Using a xp disk with 'fixmbr', will bring you more steps to do - then ya might want.

   When ya boot up...does a grub menu appear?
   What happens?

---

### Post by koopa225 on 2009-01-10
when i shut down or restart my computer it goes straight to Ubuntu

---

### Post by cerealtx on 2009-01-10
um, u might want to check your diskspace it sounds like u formated over your windows partition...

---

### Post by cerealtx on 2009-01-10
```
df
```
do that in terminal and post results

---

### Post by koopa225 on 2009-01-10
corey@Coreys-Notebook:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             75631676   2716360  69073376   4% /
tmpfs                   224024         0    224024   0% /lib/init/rw
varrun                  224024       104    223920   1% /var/run
varlock                 224024         0    224024   0% /var/lock
udev                    224024      2720    221304   2% /dev
tmpfs                   224024       780    223244   1% /dev/shm
lrm                     224024      2000    222024   1% /lib/modules/2.6.27-7-generic/volatile

If I did overwrite Windows is there away I can get the files I need? I really like Ubuntu I just want the files and i'm good

---

### Post by cerealtx on 2009-01-10
yah hommie the only partition you have is sda1 so you deleted everything that was on windows :( sorry to tell ya man, you might look at some starting guides, and look at the partitioning sections, so that you can prevent stuff like this from happening, best of luck man

---

### Post by koopa225 on 2009-01-10
thankx for all the help, I guess I gotta start my music collection all over again

---

### Post by cerealtx on 2009-01-10
it happens man, ive done it so many times its retarded, the best safe gaurd is organization using partitons [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) and sence you were talking about dual booting check this out too [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) GL

---

### Post by koopa225 on 2009-01-10
one more question, now can i install windows again since all i have is ubuntu? I still have the restore disk that came with my laptop somewhere around my crib, or should I make a liveCD for windows. I think im makin this dual boot thing a lil harder than it should be.

---

### Post by ajcham on 2009-01-10
> **koopa225 said:**
> one more question, now can i install windows again since all i have is ubuntu? I still have the restore disk that came with my laptop somewhere around my crib, or should I make a liveCD for windows. I think im makin this dual boot thing a lil harder than it should be.

Although it can be done, making a Windows Live CD is much tougher task than setting up a dual-boot.

The easiest way to dual-boot is to install Windows first. If I've understood correctly, you've only just installed Ubuntu so you don't stand to lose anything by removing it, yes?

If so, use the gparted tool on the Ubuntu Live Disc.  Delete all partitions, then create a single new partition of the size you want for Windows, leaving the rest of the drive unformatted.

Then install Windows using the disk you have - it should only install into the new partition, although some recovery discs can act differently and it may format your entire drive anyway.

If it doesn't you can then install Ubuntu, creating the appropriate linux partitions on the unformatted part of the drive.

---

### Post by cerealtx on 2009-01-10
> **koopa225 said:**
> one more question, now can i install windows again since all i have is ubuntu? I still have the restore disk that came with my laptop somewhere around my crib, or should I make a liveCD for windows. I think im makin this dual boot thing a lil harder than it should be.

yah i hear ya man, when i first started i had NO idea what partitions where or anything, i would look for that windows cd, windows has its own partitioning program aswell when installing ill tell ya how my setup is to give u a idea, on my laptop i have 120gb harddrive, 10 is for / thats root all my system files/drivers/ect, i have 50gb setup for home which is stuff i have on my computer like music videos ect and 50gb for windows c:\
thats just one idea ive had numerous diff types, u might also check into wubi , it lets you install unbuntu through windows!!  [http://wubi-installer.org/](http://wubi-installer.org/) gl man! it might be of good use to do some reading on partitioning, because if u **** up the begining, the rest is usually ****** up to :P good starts make good computers :) GL

---

