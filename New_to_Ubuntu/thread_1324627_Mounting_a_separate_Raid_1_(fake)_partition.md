---
title: "Mounting a separate Raid 1 (fake) partition"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Aceninja on 2009-11-12
Hi Guys,

I am in the process of switching from Windows to Linux (currently I have a dual boot setup) and am a bit new at this. Here is my problem, I have two different boot hdds (for Win 7 & Ubuntu) respectively. I also have 2 different hdds that have been configured as raid 1 in Bios/Windows using Intel Raid 1 setup(ICH10R). Windows recognizes it fine using Matrix Raid manager but Linux recognizes it for what it is, ie two different partitions. I have seen guides out there for mounting and installing Linux on such a partition, but since I have separate boot disks for each OS, I just need Ubuntu 9.10 to think it's dealing with one disk instead of two, ie make the Raid 1 work in Ubuntu, without making it a bootable. Can someone please help me with this? I am a noob to Linux so your help will be sincerely appreciated.

-Dilip

---

### Post by MartinEve on 2009-11-12
Firstly, welcome!

However, as a beginner, you've stumbled, I'm afraid, into somewhat tricky Linux territory.

Fakeraid support is notoriously difficult, but I'll give you some guidance from my experience of using a similar setup; it IS possible :)

I had a RAID 1 mirror setup that was comprised of 2 disks. Using the console (terminal) install dmraid:

```
sudo apt-get install dmraid
```

If you so wish, you can use the package manager to do this.

The next command you'll need is:

```
sudo dmraid -ay
```

This tells dmraid (the Linux RAID handler) to attempt to activate any RAID partitions it finds. If you are in luck, this stage will just go through!

To ascertain whether this is going to plan issue:

```
ls -l /dev/mapper/
```

and, if you see something like this:

```
control             name_of_RAID_array
```

then it has worked.

You should then be able to mount this partition using the method of your choice.

If you need further assistance, be sure to post the output of each stage of the above.

Best wishes,

Martin

---

### Post by Aceninja on 2009-11-12
Hi,

Thanks for your advice: When I type the command sudo dmraid -ay in terminal here is what I get :

RAID set "isw_ddjbfabhca_Raid 1" was activated
RAID set "isw_ddjbfabhca_Raid 11" was not activated

(RAID 1 is the volume name of the drive in Windows/Bios)

After I type in ls -l/dev/mapper:

total 0
crw-rw---- 1 root root  10, 60 2009-11-12 18:11 control
brw-rw---- 1 root disk 252,  0 2009-11-12 22:12 isw_ddjbfabhca_Raid 1


I am still seeing two partitions with the same name in the GUI..and now I am unable to mount either partition:

I get an error message saying "Error Mounting: mount exited with code 21: fuse: mount failed: device or resource busy"

I am now completely perplexed. Any help will once again be truly appreciated. 

-Dilip

---

### Post by alphaniner on 2009-11-12
For what it's worth, I played around with a ICH10R RAID0 in Karmic just a few hours ago.  This was in the standard LiveCD; I didn't install any extra packages.  I was able to partition, format, mount and write just fine.  I did get an error when installing, but I'm pretty sure it was a GRUB problem.

Are you sure you are addressing the partitions correctly?  What is the output of ```
sudo fdisk -l /dev/mapper/isw_ddjbfabhca_Raid\ 1
```

---

### Post by Aceninja on 2009-11-13
Ok,

I copied and pasted the command:

sudo fdisk -l /dev/mapper/isw_ddjbfabhca_Raid\ 1

but I get nothing, nothing at all just the blank prompt in terminal. just out of curiosity why is the 1 after the \ ?

---

