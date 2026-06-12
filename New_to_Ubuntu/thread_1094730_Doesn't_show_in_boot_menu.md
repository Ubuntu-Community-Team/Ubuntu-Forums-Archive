---
title: "Doesn't show in boot menu"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by jaguax on 2009-03-12
I just installed Ubuntu on a 25 gig partition on one of my hard drives. I manually chose the partition, formatted as ext3, chose "/" as the root, and it bugged me about making a swap space but I looked everywhere and see no option for a swap space. So I installed anyway without the swap space.

Restarted, and I get the standard Windows boot menu listing Win 7 and Vista. No Ubuntu. What gives?

---

### Post by miegiel on 2009-03-12
> **jaguax said:**
> I manually chose the partition, formatted as ext3, chose "/" as the root, and it bugged me about making a swap space but I looked everywhere and see no option for a swap space. So I installed anyway without the swap space.

You always need to make a swap partition (and a root partition). It's also a good idea to make a separate home partition.

In the manual partition section of the installation you should not only make the partitions but you should also set what the partition should be used for (root, swap, home).

---

### Post by jaguax on 2009-03-12
Hmmm... I didn't see those options. You're telling me to make 3 partitions? How big should they be?

---

### Post by jubxie on 2009-03-12
When I've had this issue in the past I have run the Super Grub cd (bootable disk) to fix the MBR. Not sure about the swap issue, but this is a great thing to have around anyway. Saved me a few times....

[http://stmaarten.globat.com/~supergrubdisk.org/](http://stmaarten.globat.com/~supergrubdisk.org/)

---

### Post by theozzlives on 2009-03-12
Root (/) at least 10 GB, swap, the amount of RAM you have, /home whatever is left (or how big you want).

---

### Post by miegiel on 2009-03-12
> **jaguax said:**
> Hmmm... I didn't see those options. You're telling me to make 3 partitions? How big should they be?

It depends on your disk size what you can spare, but here's what I have:
root : 20GB, 5.3GB used
swap : 4GB, but it never uses more then 50MB :D
home : 460GB, basically all the space left on the disk.

---

### Post by jaguax on 2009-03-12
I'm so confused. I only see two options: swap area and all the different file systems. Furthermore, the partition tool will not let me make a partition smaller than 80 gig (which happens to be the size of the used portion of the disk).

---

### Post by miegiel on 2009-03-13
> **jaguax said:**
> I'm so confused. I only see two options: swap area and all the different file systems. Furthermore, the partition tool will not let me make a partition smaller than 80 gig (which happens to be the size of the used portion of the disk).

I'm not sure but it sounds like you used all the space for your root partition. Make it smaller or delete it and make a swap (and home) partition in the space you freed up.

If you change "swap area" to "ext3" you can select mount points.

---

### Post by jaguax on 2009-03-13
I noticed in advanced options it asks where to install the boot loader. Default is something like disk0, and all the other options are my hard drives and partitions. So I tried choosing the partition that I formatted with Ext3, and it gives me a fatal error when installing the boot loader. Then I tried choosing the hard drive itself (the disk drive name/model) and I got the same fatal error.

Uggghhh. I just want to try Linux out. Why is this so difficult?

---

### Post by jaguax on 2009-03-13
Ok I just realized that there was an automatic partition option (guided install or whatever it's called). So I did that, everything was automated, and I still get the standard windows boot menu! Where is this grub thing and why won't it work?

---

### Post by nelskurian on 2009-03-13
> Ok I just realized that there was an automatic partition option (guided install or whatever it's called). So I did that, everything was automated, and I still get the standard windows boot menu! Where is this grub thing and why won't it work?

The problem you faced was not related to the swap space.I hereby point a few for your future notice.Actually swap space is a purely formal partition that the OS use this space if the system RAM overloaded.Normally the swap space utilisation is 0% in almost all machines.The rule for creating swap space is double the RAM size.You can create this partition at the partition time as the type swap in drop dowmn menu after ext3.And their is no mount potin option requird for swap space.
      the problem is that the grub may be installed in your linux partition.Normally the the grub writes to the system MBR.Its the first sector of the first disk.And also in partition time you didnt declare the / partition as bootable.check the boobtable flag as ON
       In Guided install what option you selected.The free space available or the 25GB partiiton you have.
       Also in some sysuems due to some hardware related problem the installation leads to some failures.This is mostly in newer systems due to the lack of hard ware drivers.I dont think this is your problem.Actually all the other part of OS installed in your syatem.But the grub was not installed.Grub is the routing path to the OS loader.
  So pls specify bootable flags.And their is no immediate requirement for swap space.If you have the ubuntu alternate disk,install grub in the first disk hd0 by simply selecting the system recovery option in the first menu.And if you have the live cd and the linux terminal use the 'grubinstall' command after booting the live cd.checkout below.

#sudo grub

From the grub

Type

grub> find /boot/grub/stage1

(hd0,1)

(hd0,5)

It dispay partition which contains your grub files. I have two linux OS installed.

Then run the following command

>root (hd0,1)
>setup (hd0)

(hd0) = the MBR for the hard disk which is where grub needs to install itself too for it to load on bootup.   
====================================
If the above fails you can use 
#grubinstall (hd0)


Atlast dont go away from linux due to these starting trouble .Once you have the proper linux experience You wont go away..I am sure..Sine ubuntu is in our side..thats the user side.

---

### Post by presence1960 on 2009-03-13
why don't you run this command from the live cd and post the output > sudo fdisk -l

---

### Post by jaguax on 2009-03-13
> **nelskurian said:**
> 
Then run the following command

>root (hd0,1)
>setup (hd0)

(hd0) = the MBR for the hard disk which is where grub needs to install itself too for it to load on bootup.   
====================================
If the above fails you can use 
#grubinstall (hd0)


grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition


> **presence1960 said:**
> why don't you run this command from the live cd and post the output

Note that I have two hard drives, the 750 gig and the 150 gig. The boot drive in BIOS is the 150 gig, while Ubuntu is installed on the 750 gig. Maybe that's the prob? Maybe I should set the boot drive to the 750 gig? Will I still be able to boot Windows though?

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f3fa801

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       64379   517123293+   7  HPFS/NTFS
/dev/sda2           69596       91201   173548544    7  HPFS/NTFS
/dev/sda3           64380       69595    41897520    5  Extended
/dev/sda5           64380       69376    40138371   83  Linux
/dev/sda6           69377       69595     1759086   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe3485a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18242   146520060    7  HPFS/NTFS
```

---

### Post by jaguax on 2009-03-13
lol yep I was right... I set it to boot from the 750 gig and bam there it was. I just hope I can still launch Win7 from this menu. I'm seeing two Vista/Longhorn entries in the grub menu, I'm hoping one of those is 7, heh.

Thanks a lot for all the help guys, much appreciated. :)

---

