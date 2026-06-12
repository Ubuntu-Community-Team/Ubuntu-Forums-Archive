---
title: "new to Linux\partitioning"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by js6seaj on 2009-04-17
I am brand new to Ubuntu and Linux. I am going to be building a new system with the following specifications:  Broadway Case, PC CHIPS A15G mother board, AMD Phenom 9600 Agena 2.3GHz cpu, Transcend 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) ram, ASUS EN6200LE TC1G/TD/512M GeForce 6200LE 512MB 64-bit GDDR2 PCI Express x16 Video Card, Western Digital Caviar SE16 WD5000AAKS 500GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive, and a Pioneer 20X DVD±R DVD Burner Black SATA Model dvd drive. 
When I finish building the new computer, I want to try and have a triple boot with Windows XP service pack 3, Window Vista Business 64bit with service pack 1 and Ubuntu 8.10. I am working on figuring out the best way to partition the hard drive. 
From my research so far I think I would be able to using qtparted. I have downloaded qtparted on my current computer and was reading the install file. The person who wrote the install file wrote as best as I can tell as someone who understands programming and Linux extremely well. There is only two problems with this one is I am currently taking and Intro to programming class. So, I am just learning some about programming. The second problem is I know basically nothing about Ubuntu or Linux. So, I don’t understand what the person is trying to say, they might as well be speaking German. 
Is there anyone with advice on how to install and use qtparted to set up a triple boot? I have some DOS knowledge, which may or may not be helpful. I am mostly a hardware person as you can probably tell. I am mostly familiar with Windows 98/XP, but have used Windows 3.1, 95, a little NT 3.51, and even a little OS2. I know my system may not be the best, but it is an impromant, and I would rather not have to buy partitioning software. I do know fdisk and have DOS 6.22 on floppy disk if needed. (yes, that is odd I know)

---

### Post by Bachstelze on 2009-04-17
You won't need to use any partitioning software. All you'll have to do is install both your Windows version first and make sure you don't give them the whole hard drive but install them on smaller partition in order to have frees pace available for the other OSes.

So for example:

1) Install Vista on a 150 GB partition, leaving 350 GB free space,
2) Install XP on another 150 GB parition, leaving 200 GB free space,
3) Install Ubuntu on those 200 GB.

---

### Post by js6seaj on 2009-04-17
> **HymnToLife said:**
> You won't need to use any partitioning software. All you'll have to do is install both your Windows version first and make sure you don't give them the whole hard drive but install them on smaller partition in order to have frees pace available for the other OSes.

So for example:

1) Install Vista on a 150 GB partition, leaving 350 GB free space,
2) Install XP on another 150 GB parition, leaving 200 GB free space,
3) Install Ubuntu on those 200 GB.

The hard drive would need partitions though, might be able to do this with fdisk, but DOS 6.22 has FAT 16 which means 2GB limit on any partitions created with it.

---

### Post by Bachstelze on 2009-04-17
> **js6seaj said:**
> The hard drive would need partitions though, might be able to do this with fdisk, but DOS 6.22 has FAT 16 which means 2GB limit on any partitions created with it.

You can create the partitions during the XP and Vista installation. The partitioning tools there are much more intuitive than fdisk anyway.

---

### Post by js6seaj on 2009-04-17
> **HymnToLife said:**
> You can create the partitions during the XP and Vista installation. The partitioning tools there are much more intuitive than fdisk anyway.
Ok, will have to try it. Just used to fdisk and have never really used the partitioning tools in XP or Vista. Guess I'm a little behind the times.:D But, thanks for the help and we'll see how I do.

---

### Post by sadaruwan12 on 2009-04-17
Hi,

Yo Bro in my experience don't use fdisk use XP for the partitioning part for windows and also use NTFS as your file system don't use FAT it's very troublesome and I also had installed a PC for triple boot heres the order I've used.

[LIST=1]
[*]Windos XP SP3
[*]Vista your version SP1
[*]Ubuntu v8.04LTS
[/LIST]

This order will work with out any problems.

---

### Post by js6seaj on 2009-04-17
> **sadaruwan12 said:**
> Hi,

Yo Bro in my experience don't use fdisk use XP for the partitioning part for windows and also use NTFS as your file system don't use FAT it's very troublesome and I also had installed a PC for triple boot heres the order I've used.

[LIST=1]
[*]Windos XP SP3
[*]Vista your version SP1
[*]Ubuntu v8.04LTS
[/LIST]

This order will work with out any problems.
Thanks, just some what of a DOS lover still, but at least Ubuntu has a real command line. :)

---

