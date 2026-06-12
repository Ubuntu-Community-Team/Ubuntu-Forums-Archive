---
title: "Install Ubuntu on USB pendrive"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-02-04
I want to install ubuntu on a usb pendrive. how can I do it?
I mean that I dont want to install ubuntu from a usb pendrive but on a usb pendrive so I could have ubuntu with me everywhere....
Thanks :)

---

### Post by Kirboosy on 2011-02-04
Use the "Startup Disk Creator"

System-->Admin-->Startup Disk Creator.

I would recommend 32 bit on the Thumb Drive so you can run it basically on any computer out there.


~Caboose

---

### Post by Avidanborisov on 2011-02-04
Thank you :)
But Startup Disk Creator says that it will help to try or install Ubuntu from a removable disk.
So, it will put ubuntu installation on the usb pendrive or it will install ubuntu on the pendrive?

---

### Post by Kirboosy on 2011-02-04
Oh you want to actually physically install Ubuntu to the thumb drive...

Startup Disk Creator will put the LiveCD on the Thumbdrive.

if you want to physically install it you just need a LiveCD of Ubuntu and when selecting the drive to install it to just point it to your thumb drive. Just make sure you DO NOT setup a SWAP Partition. A SWAP Partition will kill your drive.

However there is a way with StartupDisk you can let it save your settings. I've never personally tried it but I don't think it would be that hard..

---

### Post by Avidanborisov on 2011-02-04
> **Caboose885 said:**
> Oh you want to actually physically install Ubuntu to the thumb drive...

Startup Disk Creator will put the LiveCD on the Thumbdrive.

if you want to physically install it you just need a LiveCD of Ubuntu and when selecting the drive to install it to just point it to your thumb drive. Just make sure you DO NOT setup a SWAP Partition. A SWAP Partition will kill your drive.

yeah thats what I want :)
just a question - 
when I will install ubuntu to the thumb drive it will format it as ext3 or ext4 right?
if so, will I be able to access the thumb drive from windows?
cause I dont think windows can read ext4...

---

### Post by oldfred on 2011-02-04
Windows only reads the first FAT or NTFS partition on a flash drive. If you want windows to read it you have to manually format the flash drive and put a FAT drive first. I generally do not recommend FAT over NTFS but for a small flash drive it is fine. You need at least a 8GB flash drive for a full install. If 4Gb or smaller you can use persistance with the ISO install, that will let you save some data.

You will want to manually partition anyway to insure grub2 is installed to the flash drive. Grub normally defaults to sda, or usually your internal drive.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

Benefits of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

With grub2 persistant C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistant 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

---

### Post by Avidanborisov on 2011-02-04
> **oldfred said:**
> Windows only reads the first FAT or NTFS partition on a flash drive. If you want windows to read it you have to manually format the flash drive and put a FAT drive first. I generally do not recommend FAT over NTFS but for a small flash drive it is fine. You need at least a 8GB flash drive for a full install. If 4Gb or smaller you can use persistance with the ISO install, that will let you save some data.

You will want to manually partition anyway to insure grub2 is installed to the flash drive. Grub normally defaults to sda, or usually your internal drive.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

Benefits of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

With grub2 persistant C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistant 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

I dont want persistence.
I dont care if it will be encrypted either.
And I guess I can live without being able to access it from windows.

So basicly what I need to do is to select the thumb drive from the CD install? and what to choose for the filesystem, ext3 or ext4?

---

### Post by Linyx on 2011-02-04
But you should be careful about this point, when you are prompt at the last step while installing .... that step is **advanced step**, and you **should select the boot-loader to install on your Flash...**

See the screen-shot as well.... > [http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1004installation-large_008.jpg](http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1004installation-large_008.jpg)

At this point,you should select your flash-drive,so the boot-loader will install on your flash drive instead of your hdd....


Good-luck,

---

### Post by Linyx on 2011-02-04
> **Avidanborisov said:**
> So basicly what I need to do is to select the thumb drive from the CD install? and what to choose for the filesystem, ext3 or ext4?

You should select either ext-3 or ext-4...thats your choice....

---

### Post by Kirboosy on 2011-02-04
If you have a 16 GB thumb drive you could designate 8 GB to Ubuntu and format it as ext3 or 4 then the other 8 format as FAT. That way you can use your drive in Windows still.

---

### Post by Avidanborisov on 2011-02-04
> **Linyx said:**
> You should select either ext-3 or ext-4...thats your choice....

whats better?
I think I will choose ext3 because I will be able to access it from windows with ext2fsd.
other opinions?

---

### Post by Kirboosy on 2011-02-04
Nope you have a great idea. ext3 will be fine especially since you are installing it on a small drive.

I forgot about ext2fsd. Good call

---

### Post by Linyx on 2011-02-04
> **Avidanborisov said:**
> whats better?
I think I will choose ext3 because I will be able to access it from windows with ext2fsd.
other opinions?

Ext-3 and Ext-4 are both journaled, so both are better....As far as i know Ext-4 is faster as compared to ext-3, but for the little memory, i don't think it will make any difference, However, ext-4 is better....

if you want windows to access your flash,then ext-3 is better idea > [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by Avidanborisov on 2011-02-04
> **Linyx said:**
> Ext-3 and Ext-4 are both journaled, so both are better....As far as i know Ext-4 is faster as compared to ext-3, but for the little memory, i don't think it will make any difference, However, ext-4 is better....

if you want windows to access your flash,then ext-3 is better idea > [http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1004installation-large_008.jpg](http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1004installation-large_008.jpg)

OK thanks for the advice :)
another question - 
what is better for large hard drives?
I mean, I'm going to buy a new computer and I want to set dual boot with windows and I would like to access ubuntu from windows. From what I have heard ext2fsd can only support ext2 or ext3 so I am probably going to choose ext3. but will there be a big difference than choosing ext4? ext4 is really faster?

---

### Post by Kirboosy on 2011-02-04
ext4 is faster. That is why 9.10+ Ubuntu releases are way faster compared to their predecessors. 10.04 speed improvements was a result of Ubuntu developers diligence at speeding it up.

Ext4 is better all around but if you really need access from Windows to your drive you just might have to go with ext3

---

### Post by Linyx on 2011-02-04
> **Avidanborisov said:**
> OK thanks for the advice :)
another question - 
what is better for large hard drives?
I mean, I'm going to buy a new computer and I want to set dual boot with windows and I would like to access ubuntu from windows. From what I have heard ext2fsd can only support ext2 or ext3 so I am probably going to choose ext3. but will there be a big difference than choosing ext4? ext4 is really faster?

[SIZE=2]For large amount of data, i think ext-4 will be faster[/SIZE].....Check this for Ext-3 & Ext-4....[http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html](http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html)

Edit:- Its my Personal experience, Whenever the FSCK is running on ext-4, it is much faster then Ext-3, & i have used both of them....

---

### Post by Kirboosy on 2011-02-04
Actually I just had an idea...


What do you plan on doing with Windows?

If its not to intensive you could just run Windows in VirtualBox and setup a shared drive between the guest and host. Then you could have ext4 on Ubuntu but still have access on Windows :D

---

### Post by Avidanborisov on 2011-02-04
> **Linyx said:**
> [SIZE=2]For large amount of date, i think ext-4 will be faster[/SIZE].....Check this for Ext-3 & Ext-4....[http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html](http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html)

if so, is there an ext4 read write driver for windows?

---

### Post by Avidanborisov on 2011-02-04
> **Caboose885 said:**
> Actually I just had an idea...


What do you plan on doing with Windows?

If its not to intensive you could just run Windows in VirtualBox and setup a shared drive between the guest and host. Then you could have ext4 on Ubuntu but still have access on Windows :D

I need Windows sometimes for programs not available on ubuntu such as iTunes. Also this computer is public for all the family and not everyone likes ubuntu as me XD.
And I really dont like virtuallization...

---

### Post by Kirboosy on 2011-02-04
You could take the old computer then and install just Ubuntu on it and use the new computer with just windows on it when you need it :D

---

### Post by Avidanborisov on 2011-02-04
> **Caboose885 said:**
> You could take the old computer then and install just Ubuntu on it and use the new computer with just windows on it when you need it :D

forget about it :D
I will buy a new computer and I will do dual boot with windows...
please answer the more important questions... :)

---

### Post by Kirboosy on 2011-02-04
> **Avidanborisov said:**
> if so, is there an ext4 read write driver for windows?

no there isn't ext4 support. Unless someone updates ext2fsd

---

### Post by Avidanborisov on 2011-02-04
> **Caboose885 said:**
> no there isn't ext4 support. Unless someone updates ext2fsd

Well, is there any other tool?
cause I would really like to have ext4 cause it is fast but I will also need to access it from windows so I will have to go on ext3.
thats the problem...

---

### Post by Lt. Surge on 2011-02-04
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

Install this tool, format the USB Flash Drive, install.

Then go plug it into your designated computer and from the Boot in BIOS run from USB.

---

### Post by Kirboosy on 2011-02-04
> **Avidanborisov said:**
> Well, is there any other tool?
cause I would really like to have ext4 cause it is fast but I will also need to access it from windows so I will have to go on ext3.
thats the problem...

There are no more tools (that I know of)

Maybe you should revise the project and develop a new version. ;)

---

### Post by Dutch70 on 2011-02-04
Just a thought, if you do have a large flash drive, you may be able to create a separate /home partition on your usb, and make it ext2. Then you'll be able to have Ubuntu installed on ext4 but your files will be on /home formatted to ext2 so windows can read it.

---

### Post by Avidanborisov on 2011-02-04
> **Lt. Surge said:**
> [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

Install this tool, format the USB Flash Drive, install.

Then go plug it into your designated computer and from the Boot in BIOS run from USB.

I dont want the netbook edition.
anyway. I already got help about this...

---

### Post by Lt. Surge on 2011-02-04
> **Avidanborisov said:**
> I dont want the netbook edition.
anyway. I already got help about this...

The Desktop Edition installs pretty much the same way, and ok.

---

### Post by Kirboosy on 2011-02-04
> **Avidanborisov said:**
> I dont want the netbook edition.
anyway. I already got help about this...

He was just pointing to Step 2 about USB drives. haha

---

### Post by Linyx on 2011-02-04
> **Avidanborisov said:**
> Well, is there any other tool?
cause I would really like to have ext4 cause it is fast but I will also need to access it from windows so I will have to go on ext3.
thats the problem...

> [http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

But many user are Complaining about this tools that it isn't working to read-write ext-4,

What if you put your important stuff in NTFS, so that it can be Accessed by both Windows/Linux,
I have dual-booted Windows and Ubuntu and i have all my important data on NTFS Partition and i am able to access them from both....

---

### Post by Avidanborisov on 2011-02-04
> **Caboose885 said:**
> There are no more tools (that I know of)

Maybe you should revise the project and develop a new version. ;)

Sure!!! How didn't I think about it?
LOL

---

### Post by oldfred on 2011-02-04
+1 on Linyx's suggestion for NTFS partition.

When planning your partitions, you do not want to write into foreign systems. You can read from them, but do not write as that may cause problems. Create a shared NTFS partition for any data you may want in either system.

Some windows users suggest a separate data partition anyway, so when you have to reinstall windows you do not have to reinstall all your data. Backups are still required.

---

### Post by pritam_par on 2011-08-19
Installing Ubuntu on pendrive is same as installing on internal hard disk. Only thing is to do is plug in the pendrive at the time of booting from CD and select the pendrive partition at time of creating the partition. Other process is as usual.

__________________________________________

---

