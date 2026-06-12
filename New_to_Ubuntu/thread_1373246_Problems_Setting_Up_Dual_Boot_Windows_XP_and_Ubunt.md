---
title: "Problems Setting Up Dual Boot Windows XP and Ubuntu 9.04"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by ExcellentEngineer on 2010-01-05
Hello Everyone,

I am a complete novice here. I've tried using Ubuntu 9.04 from the LiveCD and just loved it. The hard drive on my laptopt just died so it is the oppertune time to install Ubuntu 9.04 permenantly on the hard drive. I have done quite a bit of reading on the subject and I am aware that the best approach is to use two separate hard drives but obviously, with a laptop, this is not an option. 

There are two partitions used for the Windows installation. Windows and all related programs are installed on the C: drive and all documents are on the D: drive. I have used Norton PartitionMagic 8.0 to generate the necessary Ext3 and Linux Swap partitions. The C: drive is a primary partition while the D: drive is an extended logical partition and the Linux Partition is also a primary partition. There is also a Primary FAT16 partition at the very beginning of the hard drive that is used for Symantec BootMagic. I install the Ubuntu 9.04 using a manual partition to install Ubuntu to the partition created by Norton PartitionMagic 8.0. Everything seems to install fine but when the system restarts, I always get a GRUB Error message (Either 15 or 17). All I can say is thank got for Norton Ghost 15.0 abs Symantec BootMagic 8.0 because that combination has saved my *** at least 10 times now. 

The system details are as follows:

The laptop is a Sony Vaio VGN-BX295VP with an Intel Pentium M 740 1.73GHz processor with 2GB RAM (upgraded from 512MB) and a 500GB SATA hard drive (upgraded from 100GB). Full specs for anything I've left out are available here [http://support.vaio.sony.eu/computing/vaio/specifications/index.aspx?m=VGN-BX295VP&l=en_GB](http://support.vaio.sony.eu/computing/vaio/specifications/index.aspx?m=VGN-BX295VP&l=en_GB). For some reason, they appear in Spanish even though it is the UK website so you will need the Google toolbay with the translate app to understand them.

Of the solutions I've tried, I removed Symantec BootMagic 8.0 in case it was causing problems with the GRUB installation but this did no good. I also tried letting Ubuntu choose its own partition parameters but this also failed. I've also gone as far as trying to use an SGD floppy to fix the problem with no luck. I've also tried to manually install the GRUB onto the same partition as the Ubuntu installation and then boot that from the SGD. I've covered every thread on these particular error codes but none of the solutions on offer have worked for me.

One possible explanation I have is that for some reason, the BIOS recognises the HDD as 137GB rather than 500GB despite Windows recognising it as a 500GB disk. Might I need a BIOS update? There are none on offer from Sony in relation to the hard drive controller so could I get a generic BIOS from somewhere else?

---

### Post by Gone fishing on 2010-01-05
I'd not use PartitionMagic but boot to the live CD and use gparted to create the partitions or delete the Linux partition and install into the largest available free space. I'd also let grub manage the booting or use GAG (which I do) and install grub onto the boot partition although with Karmic I had to make a small ext3 boot partition separate from the root ext4 partition to use GAG. It would be easiest just to let grub do it.

---

### Post by oldfred on 2010-01-05
Is this computer older? You may need a new BIOS from Sony. I doubt there is any generic BIOS. If you have this limit you may need to create a separate /boot partition within the 137GB limit.

Per Herman:
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)
**BEFORE YOU DO ANYTHING, check your computer's BIOS date and settings in case your BIOS can be updated instead.**
                                    
**                                       You can check the date of your computer's BIOS** by going into 'setup' by pressing the appropriate key during the early stages of booting, something like this: [    Getting Product Information]("http://members.iinet.net/%7Eherman546/p1.html#Getting_Product_Information").
                                     
                                     Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit _______________________________(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)____(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation _______________________(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit) _________(September 2001)

---

### Post by ExcellentEngineer on 2010-01-06
> **Gone fishing said:**
> I'd not use PartitionMagic but boot to the live CD and use gparted to create the partitions or delete the Linux partition and install into the largest available free space. I'd also let grub manage the booting or use GAG (which I do) and install grub onto the boot partition although with Karmic I had to make a small ext3 boot partition separate from the root ext4 partition to use GAG. It would be easiest just to let grub do it.

For some reason, the Ubuntu installer will not let me manually create the Ext3 partition in unallocated space. Could the reason possibly be that I need to have the Windows and the Ubuntu partition side by side? I should have mentioned that the order from start to finish of my partitions on the HDD are Symantec MootMagic (H: Drive, Primary, FAT16) -> Windows & Installed Programs (C: Drive, Primary, NTFS) -> File & Document Storage (D: Drive, Logical, NTFS) -> Currently Unallocated Space (Possibly Use for a Windows 2000 Installation Later) -> Linux (Primary, Ext3) -> Linux Swap.

---

### Post by ExcellentEngineer on 2010-01-06
> **oldfred said:**
> Is this computer older? You may need a new BIOS from Sony. I doubt there is any generic BIOS. If you have this limit you may need to create a separate /boot partition within the 137GB limit.

Per Herman:
[http://members.iinet.net.au/~herman546/p15.html#18]("http://members.iinet.net.au/%7Eherman546/p15.html#18")
**BEFORE YOU DO ANYTHING, check your computer's BIOS date and settings in case your BIOS can be updated instead.**
                                    
**                                       You can check the date of your computer's BIOS** by going into 'setup' by pressing the appropriate key during the early stages of booting, something like this: [    Getting Product Information]("http://members.iinet.net/%7Eherman546/p1.html#Getting_Product_Information").
                                     
                                     Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit _______________________________(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)____(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation _______________________(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit) _________(September 2001)

I suppose one could describe this as an older computer. It was bought nearly 4 years ago now so that would have been around 2006? I will check with Sony to see if they have any BIOS updates.

---

### Post by ExcellentEngineer on 2010-01-06
I checked with Sony and there are no BIOS updates. I will try a combination of the two approaches suggested above by disabling Symantec BootMagic (which I was probably going to do anyway), replace the small 2GB FAT16 partition currently used fro Symantec BootMagic with a boot partition for GRUB. Do I need to reformat that partition as an Ext3? Also, te get GRUB onto this partition, do I used the "Advanced" option during Ubuntu installation to redirect GRUB to this new partition? Finally, I presume I have to set the boot partion as "Active" and "Boot" in order for it to work?

---

### Post by oldfred on 2010-01-06
There is a difference between a grub partition and a boot partition. I have a grub partition but that is because I have several versions of Ubuntu installed and found chainbooting to be best. I think you just need a boot partition within the first 137GB of the hard drive. It can be any ext2, ext3 or ext4 format. When you set up partitions in advance you have to use the manual install where you choose /boot, / (root), swap and if you have /home as a separate partitions. The advanced button in the install is on where to install grub which is normally the MBR. Only if you have multiple drives or plan on chainbooting from another operating system would you install grub somewhere else than the MBR of the first drive in BIOS.

---

### Post by ExcellentEngineer on 2010-01-07
> **oldfred said:**
> There is a difference between a grub partition and a boot partition. I have a grub partition but that is because I have several versions of Ubuntu installed and found chainbooting to be best. I think you just need a boot partition within the first 137GB of the hard drive. It can be any ext2, ext3 or ext4 format. When you set up partitions in advance you have to use the manual install where you choose /boot, / (root), swap and if you have /home as a separate partitions. The advanced button in the install is on where to install grub which is normally the MBR. Only if you have multiple drives or plan on chainbooting from another operating system would you install grub somewhere else than the MBR of the first drive in BIOS.

Thanks for the advice. How do I define a partition as a boot partition? Just to update, I tried installing Ubuntu on the old 100GB hard drive I took out of this particular laptop which still kinda works. I let ubuntu shrink the D: drive by itself on the end of the drive. I manually moved the slider as to give Ubuntu the maximum amount of space I could give it. It worked no problem. I could boot both Windows XP and Ubuntu

---

### Post by ExcellentEngineer on 2010-01-11
Still no luck with setting up a dual boot on my new 500GB hard drive. Anyone any info on how to create a separate boot partition to get around the problem of my BIOS only recognising the new HDD as a 137GB drive?

---

### Post by oldfred on 2010-01-11
You have to manually partition and then use the manual install to select the partitions you have created. boot , root (/), swap  and /home if separate.

the boot partition only needs to be 100-200mb but in the first 100GB of the drive.

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

