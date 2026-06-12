---
title: "windows xp erased in ubuntu installation"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by deboh on 2009-01-25
hi anyone, i have just installed ubuntu on my system and it actually works fine although i use a dual screen with windows xp but since i got to install ubuntu 8.10 only one screem gets to display, the second is just black blank.

however that isnt the major issue here, after installation i wanted to switch over to my xp but i couldnt find windows xp anymore, my intention was to dual boot because i am a 3d animator and there isnt a linux version of one of the software i use yet-(lightwave), so keeping xp was the best option, now xp is gone, pls what do i do, i think i will love to uninstall ubuntu and see if it help or uninstall ubuntu and reinstall Xp so that i later reinstal ubuntu for dual boot, pls help what do i do or how do i uninstal ubuntu + plus GRUB which i hear is so domineering.

---

### Post by taurus on 2009-01-25
When you installed Ubuntu, did you tell the installer to use the whole disk?

Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by x33a on 2009-01-25
if you see your windows partition there, most likey sda1 with ntfs, then your xp partition may be intact.

---

### Post by deboh on 2009-01-25
YEAH, I SAID USE THE WHOLE DISK, SO I GUESS THAT WAS MY ERROR AS I WAS A NEW COMMER TO UBUNTU, BUT GUYS TELL ME PLS, THE sudo fdisk IS TYPED AS -1 AND -I WHICH IS CORRECT PLS...WHAT IF MY PATITION ISNT INTACT X33A....I REALY NEED A WAY OUT HERE, THANKS GUYS

---

### Post by taurus on 2009-01-25
If you want to reinstall window first and Ubuntu next, boot from Ubuntu LiveCD and use gparted in System -> Administration to delete all the partitions on your harddrive.  You have to click the swap partition and unmount it first before you can delete it.  Then, create two new partitions, (something like /dev/sda1 & /dev/sda2), and format the first partition to ntfs filesystem while the second one to ext3.  Save it and reboot with your windows disc in the drive.  

Now, install windows on the first partition and when it's finished, boot with Ubuntu LiveCD and install it on the second partition.

---

### Post by deboh on 2009-01-25
i dont actually wish to reinstall xp if there is another way out besaouse i will loose everything if the windows xp still exist but invisible to me.

if on the other hand it totally gone, then i have to reinstall xp first and ubuntu nest but wont i be required to uninstall ubuntu first before i can install xp? or would the partition stuff with the disk as you explained work with ubuntu still installed.

---

### Post by x33a on 2009-01-25
do as tauras instructed if you don't want more headaches. installing windows after ubuntu is much harder for less technically inclined people.

and forget about your previous windows install, there's not a chance of it being there if you did use the whole disk for ubuntu install.

so first delete ubuntu, then install windows and again install ubuntu.

---

### Post by deboh on 2009-01-25
i guess that will be the direction now, but it appears that i need the ubuntu live cd in order to be able to delete ubuntu and is that what the partition process explained does?(delete ubuntu, if thats it then i will try it out and delete ubuntu thru partitioning and then xp again  befroe ubuntu next.

---

### Post by tomtom1982 on 2009-01-25
> f on the other hand it totally gone, then i have to reinstall xp first and ubuntu nest but wont i be required to uninstall ubuntu first before i can install xp? or would the partition stuff with the disk as you explained work with ubuntu still installed.

It is possible to install xp after ubuntu, you only has to rebuild grub

BUT

If you´ve only one partition on your HDD and you´ll make a new one for your xp it will be the second partition, so you can get a xp-boot-error ("Media Error - Please insert valid boot-device").

So take a LiveCD, make a NTFS-partition for xp, a SWAP-partition for ubuntu and an ext3-partition for ubuntu (or two if you want to have a seperately /home-partition), choose "manually" and there choose the ext3-partition.

---

### Post by x33a on 2009-01-25
yes you do need a live cd, because you can't delete the current ubuntu install from within it. the live cd will help you delete ubuntu and make new partitions.

just note taurus' instructions on a paper, and keep it for reference.

---

### Post by linuxisevolution on 2009-01-25
> **deboh said:**
> i guess that will be the direction now, but it appears that i need the ubuntu live cd in order to be able to delete ubuntu and is that what the partition process explained does?(delete ubuntu, if thats it then i will try it out and delete ubuntu thru partitioning and then xp again  befroe ubuntu next.

Simply Boot the Livecd and then select System >> Patition Manager ( or gparted ). Then unmount any mounted filesystems. Next make a NTFS partition and an ext3 partition. Click apply and wait. Next put the XP cd in and restart your computer. After that is finnished install Ubuntu, but use the other partition. ;)

---

### Post by deboh on 2009-01-25
ok guys i will get back to you as soon as i figure out practically what you have advised me, thanks all.

tomtom1982, your reply is similar to taurus but you mentioned 3  partitons--ntfs,swap and ext3, i thot it was only 2, ntfs and ext3 partitions, i quote you
''So take a LiveCD, make a **NTFS-partition** for xp, a **SWAP-partition** for ubuntu **and an ext3-partition** for ubuntu (or two if you want to have a seperately /home-partition), choose "manually" and there choose the ext3-partition.
thanks

---

### Post by deboh on 2009-01-25
can you aswell help me with my second conputer not displaying right from wheni switched over to ubuntu, i use a Geforce7100 graphics card and it displayed dual screen with windows, ...?

---

### Post by x33a on 2009-01-25
the swap partition is kind of similar to the pagefile.sys in windows. just that this requires a different partition. make it equal to the size of your ram.

edit: please, start a different thread for your other graphics related problem.

---

