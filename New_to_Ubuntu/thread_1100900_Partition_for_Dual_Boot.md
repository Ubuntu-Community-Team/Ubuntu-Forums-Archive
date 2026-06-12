---
title: "Partition for Dual Boot"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by ashwat on 2009-03-19
I had Vista + NTFS. I made it into 8.10 + Ext3 totally. Then while testing 9.04, for best results I made a big chunk of it into ext4 and the remaining as FAT32 so that I could install WinXP. 9.04 is working perfectly, just that WinXP CD does not recognize that FAT32 partition saying there is no HDD. What do I do so that I can have the dual boot?

---

### Post by jlochhead on 2009-03-19
Make sure that you made the fat32 a primary partition rather than logical. Windows cannot recognise logical partitions.

If it is primary you might want to look into the fdisk command. People will probably want fdisk output for more info on your problem.

---

### Post by ashwat on 2009-03-19
Thanks for the reply. How do I check if it is logical ( I think it is but not quite sure) and how do I change it ( using gparted from the boot disk?) ?

---

### Post by jlochhead on 2009-03-19
Yea you can can check it with gparted and fix the problem using gparted on the live cd.

If a partition is logical it will appear inside an extended partition. You need to delete the logical fat32 partition, shrink the extended partition by the size of the previously deleted fat32 partition and then create the fat32 as a primary partition.

---

### Post by ashwat on 2009-03-19
> **jlochhead said:**
> 
If a partition is logical it will appear inside an extended partition. You need to delete the logical fat32 partition, shrink the extended partition by the size of the previously deleted fat32 partition and then create the fat32 as a primary partition.

By this do u mean add the deleted part to ext4 and then recreate a new partition out of it? 

Could you please be a bit more clear.

---

### Post by Helios1276 on 2009-03-19
> **ashwat said:**
> By this do u mean add the deleted part to ext4 and then recreate a new partition out of it? 

Could you please be a bit more clear.


Why not take a screen shot of what gparted is showing you and we can make it a little clearer for you by referring to your actual situation?

---

### Post by jlochhead on 2009-03-19
> **ashwat said:**
> By this do u mean add the deleted part to ext4 and then recreate a new partition out of it? 

Could you please be a bit more clear.

- Delete the existing fat32 partition.

- It should have been listed inside an extended partition (if indeed it is logical). You need to shrink (resize) this extended partition by however much you want your fat32 partition to be.

- Create a new fat32 partition using the space freed from the extended partition. Make sure that this partition is of primary type.

---

### Post by louieb on 2009-03-19
There are 3 types of partitions primary,  extended and logical.

Once you learn the purpose of each then things should become clear to you. 
Heres a page I put together  [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") 

In Gparted you will find primary and extended partitions will be named sda1 - sda4  the extended partition will show up as file system extended. Logical partitions will be named sda5, sda6 ...
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 
[Linux.com :: Dual-booting Windows and Linux the easy way (Linux.com videos)]("http://www.linux.com/feature/114157")

---

### Post by ashwat on 2009-03-19
Thanks for that link. It was a sda1 primary. I went ahead to delete the partition and remade it into a primary. I tried running the XP disc with no change. I tried taking a snapshot but was not able get it out onto the hdd ( dont know how to mount them ). What next ?

---

### Post by DaveG825 on 2009-03-19
I've had this problem before. If you say you wiped Windows off your computer or reformatted, you have a problem. Windows requires that you have the proper SATA or RAID drivers in order to install. The problem with is that setup checks your (probably non-existent) floppy drive for the drivers. As far as I've learned, you need to use a program called nLite in order to incorporate the drivers you need into the Windows Install disk image. Besides the headache that this may create, nLite is also a windows program, and I've had no luck getting it to run in Wine.

It took me a while to find all of this through Google, though there might be another way. I hope there is, because I haven't actually gone through with the whole nLite thing yet, since I haven't had the time. I am, though, getting your same problem. Windows setup gets all the drivers ready, then when it's trying to start Windows it tells me that it can't find a hard drive. Obviously that doesn't make since, I'm on a laptop. Oh well.

I wish you good luck, and if anyone as a simple, clearer way to fix this problem, I'm sure we'd all appreciate it greatly.

---

### Post by meierfra. on 2009-03-19
> Windows requires that you have the proper SATA or RAID drivers in order to install. 
+1

But there also sometime is a problem with the boot sector of a Fat32 partition created by gparted. So I suggest to use testdisk to check ( and maybe fix) the boot sector:

 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your Ubuntu desktop, and then do:

```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Fat 32 partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can your Window CD now recognize the Fat32 partition.

 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

---

### Post by ashwat on 2009-03-19
> **DaveG825 said:**
> I've had this problem before. If you say you wiped Windows off your computer or reformatted, you have a problem. Windows requires that you have the proper SATA or RAID drivers in order to install. The problem with is that setup checks your (probably non-existent) floppy drive for the drivers. As far as I've learned, you need to use a program called nLite in order to incorporate the drivers you need into the Windows Install disk image. Besides the headache that this may create, nLite is also a windows program, and I've had no luck getting it to run in Wine.

It took me a while to find all of this through Google, though there might be another way. I hope there is, because I haven't actually gone through with the whole nLite thing yet, since I haven't had the time. I am, though, getting your same problem. Windows setup gets all the drivers ready, then when it's trying to start Windows it tells me that it can't find a hard drive. Obviously that doesn't make since, I'm on a laptop. Oh well.

I wish you good luck, and if anyone as a simple, clearer way to fix this problem, I'm sure we'd all appreciate it greatly.

I wish there is some tenable solution to this because I need to have this quick. And as an aside, all the best with the Champions League Draw :P.

---

### Post by ashwat on 2009-03-19
> **meierfra. said:**
> +1


 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

That seems to be the fate of my partition  as of now. Thanks for the help though.

---

### Post by meierfra. on 2009-03-19
Could you post the output of 

```
sudo fdisk -lu
```

so we can see your partition layout?

---

### Post by ashwat on 2009-03-19
Here is the output```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    78124094    39062016    b  W95 FAT32
/dev/sda2       224829675   234436544     4803435    5  Extended
/dev/sda3        78124095   224829674    73352790   83  Linux
/dev/sda5       224829738   234436544     4803403+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by meierfra. on 2009-03-20
I suggest to put the boot flag to the Fat32 partition:

```
sudo sfdisk -A1 /dev/sda
```
(1 is the number one, not a lowercase L)

---

### Post by cornish12 on 2009-03-22
I have a computer with duel boot. I have XP and Ubuntu 8.10

I firstly installed XP fresh on the entire hard drive. I then inserted Ubuntu CD and it allowed me to reduce the size of the XP partition and create one for Ubuntu at the install.

---

### Post by JohnLM_the_Ghost on 2009-03-22
If it is SATA controller (aka AHCI) problem... then you could find BIOS setting that could change SATA to work in legacy (IDE) mode.
Not guaranteed that there is one though (especially if it is a laptop)

Refer to your motherboard manual... assuming you have one.

---

