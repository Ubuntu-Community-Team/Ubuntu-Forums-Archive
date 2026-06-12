---
title: "Installing Ubuntu 10"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by borntowin on 2010-09-23
I believe this issue must have been addressed a million times before but bear with me, I am very new to Ubuntu but would very much like to learn how to use the software. But before I can do that I should first install the software on my computer which is the core of my question and my call for help.

My computer (Dell Dimension 4700) runs on Windows XP and has two SATA drives; I will refer to them as drive 1 and 2. Drive 1 has 2 partitions (C:\ and E:\ - during installation, Ubuntu identified these partitions as /dev/sda1 and /dev/sda5 respectively). Drive 2 also has two partitions (D:\ and F:\ -Ubuntu identified these as /dev/sdb1 and dev/sdb5 respectively). The file type for both drives is originally NTFS 

Windows XP is installed on C:\ and I would like to install Ubuntu 10 on partition D:\

I have already downloaded the Ubuntu 10 software and burned it to a CD. I am able to run the software from the CD so I have a functional CD.

During installation (step 4: Prepare disk space), Ubuntu elected to install itself side by side Windows XP; setup chose "Install them side by side ..." option. It carved 96.5GB of space out of the total 209.8GB from the C:\ partition to be allocated for installing Ubuntu (leaving 113.3GB for Windows XP). However, since I wanted to install the software on partition D:\ (or dev/sdb1), I opted for the Manual Partition option. 

This option took me to Step 5 where the setup listed a graphic presentation of sda1 (ntfs, 209.8GB in green) and sda5 (ntfs, 110.3GB in brown/red). In addition, there was a table in which all the partitions were listed, as shown below. 

The list of partitions in a table form looked like this:
DEVICE       TYPE              MOUNT POINT         FORMAT              SIZE                          USED
-----------------------------------------------------------------------------------------------------
/dev/sda
 /dev/sda1,    ntfs ,                                                                                                        , , 209769MB,            19438MB            
 /dev/sda5,              ntfs , , ,                                                                                                         110292MB,             21306MB

/dev/sdb
 /dev/sdb1,             ntfs , , ,                                                         55142MB,                3312MB
 /dev/sdb5,             ntfs , , ,                                                       104855MB,             10576MB

I believe because I chose the manual partition option, Ubuntu wanted me to select my own partition within sda1 instead of the automatic repartition it chose when setup selected the "Install them side by side ...". At this stage (still in Step 5), I highlighted the /dev/sdb1 partition and clicked on the "Change" option. This brought up the "Edit Partition" dialogue box which had the following components:

 - New Partition size: (where it showed the disk size 55142MB with up and down arrows where I can decrease the disk size; the up arrow was greyed out since it showed the max disk size)
 
 - Use as: (clicking the arrow lists a whole range of file types including Swap area, FAT 16/32, XFS, JFS, Ext2 file system, Ext3 and Ext4 journaling file systems)

 - Format the partition: (with a box, where one has the option to check the box to format disk or leave partition as is)

 - Mount point: (with options including: /, /boot, /home, /tmp, /usr, /var, /srv, /opt, /usr, /local)


I got stuck at this point and did not go further because I did not know exactly what to do. Do I allocate the whole disk space (55142MB) in the new partition option or I should reduce the size so as to leave some space for swap?

From my readings on Ubuntu forums, I think I should select the Ext4 journaling file system in the "use as" option but then again at what point do I get to create a swap file? Does that come later? I also read on the Internet that it is not advisable to check the "Format the partion" box; it is better to leave the box unchecked. Can somebody confirm this for me? Lastly, I am not too sure about the "Mount point" option. I would very much want to have an option at startup to select either Windows XP or Ubuntu (I guess this is what is called dual boot) and so which of the mount point options do I choose so that I can dualboot Windows XP and Ubuntu?

Since this last screen is Step 5 of 8, there are three more steps to go but I don't know what they would be. I would also appreciate advice as to what comes in the next 3 steps and what I should do. Thank you in advance for your help.

---

### Post by SaintDanBert on 2010-09-23
You've written a lengthy post and I feel compelled to really study things before I answer more completely.  However, I'm struck by a couple of things.

Partitions named xxx1-4 are "primary" partitions, while xxx5+ are "logical" or extended partitions.

Linux installers are very adept at working around whatever it finds in place on the workstation of interest. Thus it will try to step around the winXX(s) it finds on whatever partitions are present. NOTE -- WinXX expects to own the box and will gladly stomp all over existing partitions.  Therefore, [highlight]always install winXX then linux[/highlight].

You can format any partition that you no longer care about and install linux there. You can also use **gparted** and move things around or make changes. Unless are reworking the entire drive, I prefer to mess with partitions from a live-CD or similar rather than do it inside the linux installer. I then point the installer at the partitions I've already established.

You have winXX and space for win-doze data files.
You want to add linux and space for linux data files.
You have two physical drives. How do you want to deploy the space?

I might configure one OS+data on each drive. You can easily configure GRUB to dual boot during linux install. (You can also configure win-doze to dual boot if you know how.) Linux will gladly read+write your win-doze NFTS file systems. There are 3rd party tools that permit read-only access to EXT2/EXT3 from win-doze. There are other 3rd party parts that let win-doze play read-write.

I hope this helps.  Ask if you need more details.

~~~ 0;-Dan

---

### Post by sikander3786 on 2010-09-23
Quite a lengthy post and a lengthy response by SainDanBert. :-)

You want to install Ubuntu to the D: drive of Windows, means the one recognized as sdb1 by Ubuntu. And the drive is empty I assume. So delete that partition (it can easily be done by the partitioner in Ubutnu installer, use gparted if you prefer). For a basic setup you need following partitions at least.

Size > File System > Mount Point
512MB > ext3 > /boot
30-50 GB (You can use whatever size you want) > ext3/ext4 > /
RAM X 2 > Swap > Swap

You can have seperate /home partition if you like to.

There will be no difficult questions after this in the installer. :-) After it comes the personal details page and then the confirm page only. So no worries.

Ubuntu is very good at dual booting as mentioned in the above post, just at the last stage, I think step 7 it is, click the advance button and make sure that "Install Bootloader" is ticked and it is going to be installed to sda1. It will automatically pick up Windows and let you select between Ubutnu and Windows when you boot.

And it is always a good idea to format the partition. Not to format is advised only in those cases where data is involved.

Hope you get it all. ;-)

---

### Post by Elfy on 2010-09-23
When you reach the partition part of the install - choose manual as you have.

You'll need a swap and / partition at least. Mightbe worth also having a /home partition. There's not really any need for a /boot partition if you are just installing at home.

Swap depends on RAM and whether you want to hibernate - to give a sensible swap size people will need to know that.

You will have to format whatever partition you are wanting to install to.

There is a partition editor on the livecd in the sys admin menu (either called gparted or partition editor) you could do the partition work there and then pick the / and /home partitions during the manual partition part of the install.

---

### Post by sikander3786 on 2010-09-23
> 
There's not really any need for a /boot partition if you are just installing at home.


Not needed really but for me, better to have a separate /boot to keep my boot stuff separate unlike Windows. I have also seen reports that it speeds up the boot process however never compared it myself.

---

### Post by borntowin on 2010-09-23
Thanks Sikander3786 for all the advice and directions. I will give it a shot tonight and I hope it will be well. However, if I do come across any problems I will come back to ask for further guidance but as it now the instructions seem clear enough.

Actually, I forgot to mention the RAM in my computer: I have 4GB RAM which is accurately reported in BIOS but Windows report 3.25GB -- we all know why! Which means I should be looking at setting aside 8GB for Swap

Thanks once again.

---

### Post by borntowin on 2010-09-23
SaintDanBert,
Thanks for taking time to respond to my unusually long post. I thought I needed to lay out the entire thing to give reviewers a better sense of where I stand. From the partition naming system, it looks I have 2 primary and 2 logical/extended partitions and I want to install Ubuntu on the 2nd primary partition (WindowsXP is already on the 1st primary partition). I want to devote the whole partition (D:\ or /dev/sdb1) to Ubuntu.

I don't know much about this win-doze thing for dual booting so I think I will use "Mr" GRUB which seems to be the preferred option.

I guess what I should do is move ahead with the installation and report back if I encounter any problems. I will surely call on you when necessary. Thanks.

---

### Post by Elfy on 2010-09-23
> Which means I should be looking at setting aside 8GB for SwapI think you'll find you'll never use it - at most I would have just over 4Gb for suspend if you use it.

---

