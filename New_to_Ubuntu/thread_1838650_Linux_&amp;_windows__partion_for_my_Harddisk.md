---
title: "Linux &amp; windows  partion for my Harddisk"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by katochd46 on 2011-09-04
Please answer the following questions.

One thing which is confusing me is, initially 
2> Windows was installed on the PC.
3> And now linux is also installed there.
4> Now after when i start up the pc it shows me the bios operation. Then it gives me the message that GRUB is loading.
Initially there was nothing called **GRUB** on my PC **:?:**
Then it will give me a selection option, which operating system to load. How it comes to know about how many operating system is there in my PC. Is this information is held in MBR of Harddisk **:?:**


My harddisk drive is 80 GB. Also when PC is started if you can see in the** attached image file** that following two commands ;
$ sudo fdisk -l
$ sudo gparted /dev/sda 

Is refering the full harddisk as SDA divided into two part
SDA1  -- filesystem as **NTFS** 
SDA2  -- filesystem as extended (_**extended file system of linux**_) 

As per getparted : Under **SDA2** which is an extended file system of linux -- there are more partition like **sda5,sda6,sda7,sda8, sda9**
Is this right **:?:**

If this is right then **how can ** an **SDA2** partion which is of type extended file system of linux. Can have **partion like sda5,sda6,sda7 which are NTFS type** **:?:**


Also one more unique thing is that, on the panel of my desktop there are three options :
Application, **Places**, System

If i select the option such as places then, it becomes more confusing. It shows me the option for 11GB, 17GB, 21GB, 21GB file system. If we click on these it ask for pasword to **mount** the drives. Same like **sudo mount command**.

See for an 80 Gb hardisk :
gparted, fdisk are showing alsmost same thing.
But **places** on the panel of my desktop showing diffrent partion drives there.

What actually is the concept behind it **:?:**


Also how windows is able to manage from this new confusing partitions created by linux on the harddisk where previously data was created by diffrent user in diffrent DRIVES **:?:**

---

### Post by Seq on 2011-09-04
> **katochd46 said:**
> Please answer the following questions.

One thing which is confusing me is, initially 
2> Windows was installed on the PC.
3> And now linux is also installed there.
4> Now after when i start up the pc it shows me the bios operation. Then it gives me the message that GRUB is loading.
Initially there was nothing called **GRUB** on my PC **:?:**
Then it will give me a selection option, which operating system to load. How it comes to know about how many operating system is there in my PC. Is this information is held in MBR of Harddisk **:?:**

'GRUB' is the bootloader used by Ubuntu. Grub's purpose is simply to know how to start linux while being small enough to sit in the empty space at the start of the disk before your first partition. It is needed because linux is far too large to do that itself.

When grub starts, it reads a file '/boot/grub/grub.cfg' from your linux partition. That file contains all the entries that are presented in the boot-time list. It is built (automatically, usually when you run updates) by a utility called 'update-grub'. It probes your hard drive to see if there are any recognizable systems, causing Windows to be added to the list.

Windows uses a bootloader as well, it just acts differently (and is pretty much invisible to the user).

> **katochd46 said:**
> My harddisk drive is 80 GB. Also when PC is started if you can see in the** attached image file** that following two commands ;
$ sudo fdisk -l
$ sudo gparted /dev/sda 

Is refering the full harddisk as SDA divided into two part
SDA1  -- filesystem as **NTFS** 
SDA2  -- filesystem as extended (_**extended file system of linux**_) 

As per getparted : Under **SDA2** which is an extended file system of linux -- there are more partition like **sda5,sda6,sda7,sda8, sda9**
Is this right **:?:**

If this is right then **how can ** an **SDA2** partion which is of type extended file system of linux. Can have **partion like sda5,sda6,sda7 which are NTFS type** **:?:**

An extended partition isn't a linux thing. The mbr disk format can only handle four partitions. Lots of people needed more than that, so 'extended' partitions were created. They contain a bunch of 'logical' partitions inside them. Logical partitions always start at 5 (sda5+) to illustrate that they are not 'primary' partitions.

A logical partition can be any filesystem, including NTFS. It is possible that sda5, sda6, and sda7 are additional drives in Windows (D:, E:, and F: maybe). Or possibly a recovery partition.

> **katochd46 said:**
> Also one more unique thing is that, on the panel of my desktop there are three options :
Application, **Places**, System

If i select the option such as places then, it becomes more confusing. It shows me the option for 11GB, 17GB, 21GB, 21GB file system. If we click on these it ask for pasword to **mount** the drives. Same like **sudo mount command**.

See for an 80 Gb hardisk :
gparted, fdisk are showing alsmost same thing.
But **places** on the panel of my desktop showing diffrent partion drives there.

What actually is the concept behind it **:?:**

'places' is showing four NTFS filesystems. It says 21GB instead of 19.53GB because it is using SI values (x1000) instead of binary values (x1024).

[LIST]
[*]17GB -> sda1
[*]2x 21GB -> sda5 and sda6
[*]11GB -> sda7
[/LIST]

> **katochd46 said:**
> Also how windows is able to manage from this new confusing partitions created by linux on the harddisk where previously data was created by diffrent user in diffrent DRIVES **:?:**

Windows won't have a problem. You said you had different drives? I'm guessing three additional ones? You still have those, just as Windows made them. Windows made the extended partition, too.

My guess is that you originally had three 19.5GB partitions. When you installed Ubuntu, it shrank the third one to 10.17GB, then used the extra 9.3GB of space to give itself a filesystem and a small swap partition.

---

### Post by katochd46 on 2011-09-04
> My guess is that you originally had three 19.5GB partitions. When you installed Ubuntu, it shrank the third one to 10.17GB, then used the extra 9.3GB of space to give itself a filesystem and a small swap partitio

Initially i have 4 drives in windows :
**C,D,E,F**

So where is my Linux operating system executable, is it in SDA1 **(as sda1 flag is BOOT in picture attached**)or ext2 :?:

Please suggest.

---

### Post by puntigamer on 2011-09-04
> **katochd46 said:**
> Initially i have 4 drives in windows :
**C,D,E,F**

So where is my Linux operating system executable, is it in SDA1 **(as sda1 flag is BOOT in picture attached**)or ext2 :?:

Please suggest.


You should be able the see those partitions in your Ubuntu system! I think that the executable?? is on the boot partition (MBR) of your SDA1 by default. (you had to select it during the installation)
You can see and mount them using nautilus (the file manager) with clicking on them

In the GRUB there are no executable files, just information about the boot-loaders, which can load the selected OS.

---

### Post by candtalan on 2011-09-04
one confusing thing is that windows calls a partition as a 'disc'. windows drives c,d,e (etc) are often only partitions, all in one single hard drive, and are not 'drives' as suggested by windows.

ubuntu (based on gnu/linux) calls a hard drive something different to a partition. 

because of the limitation of allowing only 4 partitions, then historically a special partition type was invented which could be expanded - an extended partition type, this can have more partitions inside it.

the maximum 4 original partitions were the called primary partitions, and the extended type would contain logical partitions. both primary and logical partitions act the same for almost all functions.

hth

---

### Post by Seq on 2011-09-04
> **katochd46 said:**
> Initially i have 4 drives in windows :
**C,D,E,F**

The Ubuntu installer shrank your "F" drive, and used the extra space to install itself. You still have four drives in Windows.

> **katochd46 said:**
> So where is my Linux operating system executable, is it in SDA1 **(as sda1 flag is BOOT in picture attached**)or ext2 :?:

Please suggest.

In my last post I noted Windows has a bootloader as well. It actually uses the boot flag to decide which partition to boot. The boot flag doesn't matter to Linux, though.

*All* of your linux files are on sda8. A small bit of grub is in the MBR before the first partition, the rest of it (and it's configuration) is in sda8 with Linux.

---

### Post by katochd46 on 2011-09-05
> *All* of your linux files are on sda8.But sda8 is an logical partition inside the extended partiton scheme. Most of the document which i read i found that Operating system is loaded on the primary partition.

[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

Is it pssible that we can have O.S installed on Logical partion of a hard drive :?:

---

### Post by oldfred on 2011-09-05
To understand a little about multibooting look at this site. It is primarily about windows but really applies to MBR(msdos) systems and how they work.
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Windows first install (and the one that actually boots) has to be to a primary partition (sda1 thru sda4), but all Linux install and a second Windows install can be to a logical partition.

---

### Post by Seq on 2011-09-05
> **katochd46 said:**
> But sda8 is an logical partition inside the extended partiton scheme. Most of the document which i read i found that Operating system is loaded on the primary partition.

[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

Is it pssible that we can have O.S installed on Logical partion of a hard drive :?:

It is possible to have Linux installed and boot from a logical partition, yes.

From memory, Windows' bootloader looks for the first primary partition with the boot flag, and chainloads a partition bootloader. This may have changed with vista or 7, though.

Grub on the other hand doesn't care if it is a logical or physical partition. It also doesn't care about the boot flag.

---

### Post by katochd46 on 2011-09-07
Thanks for clarifying the above points.
 
one **last thing** which is confusing me is that,
 
BIOS is saved on on external ROM chip on the motherboard also everywhere on net it is mentioned that it is first software run by computer. But how does cpu run the BIOS because it is lying on external Memory on mother board:?: What we need is that we bring the instruction written on Bios to CPU to execute. So is there come small instructions code stored inside CPU whose job is to bring the instruction from Bios chip inside the Ram & pass control to it :?:
 
**What i guess is :**
As we know that on power on RESET & CPU jumps to reset handler. This reset handler is written inside the CPU meory whose job is to bring instruction from BIOS inside RAM& pass control to it.
 
 
 
**Please clarify this point.**

---

### Post by candtalan on 2011-09-07
> **katochd46 said:**
> Thanks for clarifying the above points.
 
one **last thing** which is confusing me is that,
 :-)  no problem
>  BIOS is saved on on external ROM chip on the motherboard also everywhere on net it is mentioned that it is first software run by computer
 yes, as I understand it.
> But how does cpu run the BIOS
 I would say (from limited knowledge) that the bios runs (itself), and at this early stage, the cpu simply controls sending video signals to the video (card) chip. I believe (?) that the cpu takes on more complex functions later, for example, after the bios has caused the MBR to be read (ie hard drive activity), and the boot loader then runs.[/QUOTE]

Any other knowledge, people, please?
hth

---

### Post by katochd46 on 2011-09-07
I found a very useful link for my last question :
 
[http://stackoverflow.com/questions/5300527/do-normal-x86-or-amd-pcs-run-startup-bios-code-directly-from-rom-or-do-they-copy](http://stackoverflow.com/questions/5300527/do-normal-x86-or-amd-pcs-run-startup-bios-code-directly-from-rom-or-do-they-copy)
 
>  
When the processor comes out of reset, it begins executing instructions at a fixed address in memory, called the "reset vector". The BIOS flash chip is mapped to this address in memory. The processor simply starts executing instructions from this address.

 
What do we mean by Bios flash chip is mapped to this address :?:
 
Please suggest .

---

### Post by anewguy on 2011-09-07
Let's say memory addressing begins at 0.  This is addressing now, doesn't mean any memory yet.  Let's say your BIOS sits in a memory block beginning with address 0.  Let's say you CPU executes the instruction starting at memory address 0.  The BIOS would then have code in it that is executed an instruction at a time until it has "control", then it can do what it wants (test the system, etc.).

Dave ;)

---

### Post by YesWeCan on 2011-09-08
> **katochd46 said:**
> Thanks for clarifying the above points.
 
one **last thing** which is confusing me is that,
 
BIOS is saved on on external ROM chip on the motherboard also everywhere on net it is mentioned that it is first software run by computer. But how does cpu run the BIOS because it is lying on external Memory on mother board:?: What we need is that we bring the instruction written on Bios to CPU to execute. So is there come small instructions code stored inside CPU whose job is to bring the instruction from Bios chip inside the Ram & pass control to it :?:
 
**What i guess is :**
As we know that on power on RESET & CPU jumps to reset handler. This reset handler is written inside the CPU meory whose job is to bring instruction from BIOS inside RAM& pass control to it.
 
 
 
**Please clarify this point.**
The BIOS program is in ROM. ROM is identical to RAM except it is read-only (in normal use). So the BIOS ROM exists in the addressable memory space of the CPU just like the RAM.

---

