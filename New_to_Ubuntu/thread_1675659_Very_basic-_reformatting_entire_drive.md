---
title: "Very basic- reformatting entire drive"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by oechsner1 on 2011-01-25
[SIZE=2]I am attempting to reformat my entire internal 160GB drive and have used the following command:  [/SIZE][FONT=&quot][SIZE=2]dd if=/dev/urandom of=/dev/sda

It has been formatting since last Thursday.  I then got impulsive and "deleted" the partition or so I think I did.  Now when attempting to format the partition again using the directions in [https://help.ubuntu.com/8.04/hardware/C/disks.html](https://help.ubuntu.com/8.04/hardware/C/disks.html)[/SIZE]  I am unable to start gparted and get the message:
E: unable to locate package gparted 
from my USB flash drive

Suggestions?
[/FONT]

---

### Post by srs5694 on 2011-01-25
First, your "reformatting" of the drive was in fact randomizing the entire disk's contents. This takes a long time because random number generation is not instantaneous, so the computer was actually doing a lot of work for every byte written to the disk. If you wanted to completely blank the disk for security reasons, using /dev/zero rather than /dev/urandom would have worked about as well and be a *lot* faster (one could debate the merits of one vs. the other, but unless you're the NSA, CIA, or whatever, the difference in security is likely to be 0).

Second, by blanking the entire disk (/dev/sda) vs. a partition (/dev/sda1 or whatever), you also eliminated the partition table, so you have no more partitions on the disk.

Third, if you just wanted to delete your partitions in order to re-install your OS fresh, simply using GParted or some other partitioning tool from the start would have been sufficient; there's no need to blank the disk first.

So, getting to your current situation, if you're using an Ubuntu installation on your USB flash drive, you should be able to install GParted by typing "sudo apt-get install gparted". Alternatively, you could try an Ubuntu install CD/DVD; just tell it you want to try Ubuntu to boot into the "live CD" mode rather than install. I'm not sure offhand precisely what partitioning software is available directly off the disc, but there's got to be something you can use. If you plan to install Ubuntu fresh, you should be able to just boot it straight into its installation mode.

---

### Post by oechsner1 on 2011-01-25
Whether booting from the flash drive or CD, I continue to get the same message when trying to run gparted:
[FONT=&quot]E: unable to locate package gparted

I want to format the drive for NTFS.  Following these directions:

[/FONT]**Partitioning a device**

                                                                           	      You can use **GNOME Partition Editor** to partition storage devices. Install the **gparted** package 	      (see [Add Applications]("https://help.ubuntu.com/8.04/add-applications/C/")) and then press System &#8594; Administration  &#8594; Gnome Partition Editor to start the partition editor. 	    
                                                                                                         [IMG]https://help.ubuntu.com/8.04/images/admon/caution.png[/IMG]                                              
                                                                                         Be careful when altering disk partitions, as it is possible to lose your data if you delete or change the wrong partition.
                                                                                
                                                                                                         **Freeing space for a new partition**

                       
                     
                   
                    		To create a new partition inside an already partitioned 		device, you must first resize an existing partition. If you already 		have free space, skip to [the section called “Creating a new partition”]("https://help.ubuntu.com/8.04/hardware/C/disks.html#creating-new-partition"); otherwise, follow the instructions below: 		
                                        
[LIST=1]
[*]                          		      Press System &#8594; Administration  &#8594; Gnome Partition Editor. 		    
[*]                          		      Select the device to partition from the drop-down list 		      at the top-right of the main window. 		    
[*]                          		      A list of partitions will appear. Select the desired partition 		      and choose Partition &#8594; Unmount. 		    
[*]                          		      To resize the partition choose 		      *Resize/Move*. The dialog 		      *Resize/Move* will be shown. You can 		      use the *Free Space Following (MiB)* 		      box to choose how much space to free after this 		      partition, or *Free Space Preceding 		      (MiB)* to free space before this partition. Alternatively 		      you can use the slider to adjust the partition size. 		    
[*]                          		      To apply the changes, click 		      **Resize/Move**. 		    
[/LIST]
Gnome Partition Editor is not available?
                  

[FONT=&quot] 
[/FONT]

---

### Post by ruegore on 2011-01-26
Is your sources list messed up?

You can use gparted from an Ubuntu Live CD.

---

### Post by HermanAB on 2011-01-26
Howdy, 

fdisk should be installed by default, ditto mkfs.ntfs.

So, read the man pages of fdisk and mkfs, then do something like this:

$ sudo fdisk /dev/sdb
n
p
1
w

and:
$ sudo mkfs.ntfs -Q -q -L NTFSDISK /dev/sdb1

---

### Post by lavinog on 2011-01-26
Which version of ubuntu are you booting with?
What is your intention of using NTFS?  Why not use windows to create this partition?

---

