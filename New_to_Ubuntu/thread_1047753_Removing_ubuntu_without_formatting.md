---
title: "Removing ubuntu without formatting"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Gennn89 on 2009-01-22
hey I need to take ubuntu off my dual boot so that i can solely run windows and free up some harddrive space but I dont know how to remove the partition or the os off there completely. i dont think i know how to make the live cd delete it so someone tell me the best way to go about this so that my friend can have his computer with only windows on it

---

### Post by 2hot6ft2 on 2009-01-22
First for windows to be able to use the drive space you free up by removing ubuntu you'll HAVE to format it to something windows can read and write to which is generally NTFS these days. This would be a separate partition from the one windows is installed on so you wouldn't be formatting windows.

Reverting to Windows - Format to NTFS
Boot from the livecd and once you're at the live desktop go to
System>Adminstration>Partition Editor
right click on the swap partition and select swapoff
right click again and select delete partition
right click on the ubuntu partition and select delete
click on the drive which should have a lot of space now and click on New
select Primary or Logical for type
Right click on it again and select Format to>NTFS

And then click on Apply
And to get rid of the Grub boot loader.
> **Monotoko said:**
> Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

That will fix XP right up :)
Should be the same with vista as it is with xp.

---

### Post by Gennn89 on 2009-01-22
thanks for that i think itll work

---

### Post by 2hot6ft2 on 2009-01-22
You're welcome. If you don't have a windows disc you can get a free vista recovery disc here. [http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)

Just select 32 or 64 bit depending on your OS. It can't be used to install vista, it's just for recovery.

---

### Post by sambront on 2009-02-15
Do you have to get rid of GRUB, or can you just leave it (even though it won't work, really).


> **2hot6ft2 said:**
> 

And to get rid of the Grub boot loader.

Should be the same with vista as it is with xp.

---

### Post by NightwishFan on 2009-02-15
You would want to use the Window MBR I think. So to remove grub/restore windows mbr you can use windows recovery or super grub disc.

Just to clarify, make sure you only delete Linux partitions. Windows is marked NTFS or FAT.

To check your partitions in Ubuntu, open a terminal and run:
```
sudo fdisk -l
```

---

### Post by sambront on 2009-02-15
This machine originally came with Vista installed. I added a second harddrive, and split it into two partitions: the first had some Windows data, and I put Ubuntu Studio on the second.

So my plan is to just remove the Ubuntu partition from within Windows, then combine both partitions on the second drive, then format that as NTFS.

Eventually I'll nuke the whole machine, but for now I would rather just keep GRUB, knowing Ubuntu choices won't work, and choose Vista when I boot (which is rare, since I leave the machine in S3 most of the time).

Essentially, I would rather leave GRUB and not risk my Windows partition at this time. I've had some bad experiences with removing GRUB.

 

> **NightwishFan said:**
> You would want to use the Window MBR I think. So to remove grub/restore windows mbr you can use windows recovery or super grub disc.


---

### Post by NightwishFan on 2009-02-15
I see. Generally it is good to not agitate the disks when using that OS. I will say that super grub fixed my Windows XP MBR automatically when I removed OpenSuse. I am not sure about how it works with Vista though.

---

### Post by sambront on 2009-02-15
So I guess my question is will simply killing the partition that Ubuntu is on "agitate" the disk?

I assume GRUB doesn't care, unless I choose an OS that does not exist.


> **NightwishFan said:**
> I see. Generally it is good to not agitate the disks when using that OS. I will say that super grub fixed my Windows XP MBR automatically when I removed OpenSuse. I am not sure about how it works with Vista though.

---

### Post by arpanaut on 2009-02-15
> Essentially, I would rather leave GRUB

Not going to work...
Grub uses files on the / partition of the Ubuntu install to facilitate booting the various OS's so if you delete/purge your Ubuntu install/partition then GRUB will not have what it needs to boot anything.

I understand your reluctance to alter your windows part. but to achieve what you seek that will be necessary.

---

### Post by bodhi.zazen on 2009-02-15
Depending on how you installed Ubuntu see :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927) 
 
    wubi : [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

Those links will walk you through restoring Windows.

---

### Post by sambront on 2009-02-21
Ok, so what about changing the partition size of the Ubuntu install? Can I shrink that, freeing up space?

I really, really want to avoid having to do anything with GRUB right now.

> **arpanaut said:**
> Not going to work...
Grub uses files on the / partition of the Ubuntu install to facilitate booting the various OS's so if you delete/purge your Ubuntu install/partition then GRUB will not have what it needs to boot anything.

I understand your reluctance to alter your windows part. but to achieve what you seek that will be necessary.

---

### Post by krzysz00 on 2009-02-21
If you have Vi$ta go here:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
You need to run Bootrec.exe with /FixMbr and /FixBoot

---

