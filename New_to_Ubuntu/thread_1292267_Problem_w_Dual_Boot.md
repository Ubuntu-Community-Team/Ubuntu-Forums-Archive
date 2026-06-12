---
title: "Problem w/ Dual Boot"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by jadams_35 on 2009-10-15
Hello,

I am trying to setup a dual boot vista/ubuntu 9.04 on my laptop. I'm not quite ready to get off windows all together.

I put the ubuntu disk in, and follow the on-screen instructions until I get to the partitioner. Once there, I selected a partion scheme that will support the two os's and supplied adequate space. Afterward, the partitioner gave a message saying it needed to do some work on the disks prior to continuing. 

The partitioner never budged off of 0%. After some time, the install process displayed a message saying to remove the disk and press enter to continue. I did so. The machine just powered off. Upon restarting (manually pushing the power) the machine jumps right to vista.

I've put the install disk back in a couple of times and Ubuntu starts the install process over again. It never gets back to the partitioner though, it gets to the 'where are you' screen for specifying time zone, then afterward, displays the 'remove the disk' screen and hit enter to continue. Ubuntu shuts off the machine. When I reboot, its back to visa (no opportunity to choose). Rinse. Repeat.

In vista, it shows the disk usage to be quite high. Instead of showing the max capacity reduced because of the additional partition, it just shows the space as used.

So, i'm guessing the additional partition exists in some fashion.

I also can't seem to get back to the partioner.

Does anyone have advice on how to proceed to get the install repaired?

Many thanks in advance.

---

### Post by |Mitch| on 2009-10-15
If you burnt the image yourself, maybe a corrupted burn. Try burning at a slower speed, 4x or below. That's all I can think of...

---

### Post by mike555 on 2009-10-15
you said you put the disc in and started the install .....  did you restart the computer to the cd , or just try installing from inside Windows?

you should put the cd in and restart your computer then run Ubuntu live for a while to make sure everything works , then click the install icon. it will let you pick "manual" partitioning where you can set a size for the Ubuntu install (you might want to split the Windows partition in half or not, just make sure you give Ubuntu enough room) set that partition as " / " , then set a swap partition (about 2 gb should be enough) then let it install.

if this is what you did , then maybe it is a bad burned disc or there might be finger prints on it ..

---

### Post by mike555 on 2009-10-15
if you think Ubuntu is installed to a partition , you could check by putting the Ubuntu cd in restarting your computer and running live, if you see the partition you think Ubuntu is installed on , mount it and see if it looks like everything is there .......

---

### Post by Jason Cook on 2009-10-15
You could try using [wubi]("http://wubi-installer.org/"). It will install ubuntu from windows and allow you to choose which operating system to use on startup.

---

### Post by jadams_35 on 2009-10-15
I've tried reinstalling again. This time I made it to the partitioner again. I was not given the option to dual-boot it. It was an either or proposition, replace the ntfs with ubuntu, or go into advanced. I surely don't know enough about partitioning linux to go into advanced.

Of interest is a bootsect.bak file located on my c: disk. There's a bunch of garbage in the file. In the middle of the garbage are the following lines:

A disk read error occurred 
BOOTMGR is missing 
BOOTMGR is compressed 
Press Ctrl+Alt+Del to restart
             €²Ê  Uª B O O T M G R  $ I 3 0  Ô   $   

I'm going to give it a try to install from windows, where it starts up the partition manager. I'll post.

---

### Post by jadams_35 on 2009-10-15
Live would not boot. It has booted in the past. :(

---

### Post by jadams_35 on 2009-10-15
Ok, the bootsect.bak was created by wubi while attempting to install ubuntu in windows. It just created that file again while trying to install with the option to select at boot which os to boot.

---

### Post by jadams_35 on 2009-10-15
Ok, so installing via wubi failed. After reboot, I selected ubuntu, went through verifying the installs and it started writing the etc3 before turning itself off.

In the c: were two files, wubildr and wubildr.mbr. wubildr had no human readable info. wubidler.mbr (master boot record?) had this to say in the midst of a bunch of garbage:

Press space bar 
Press   to start GRUB, any other key to boot previous MBR ... 
Timeout :      
Invalid previous MBR. Press any key to start GRUB ... 
Cannot find GRLDR.  to hold the screen, any other key to boot previous MBR ... 
Error while reading MBR of  drive (hd0 )  
Invalid boot indicator in partition table of  
Invalid sectors_per_track in partition table of  
Invalid start_sector in partition table of  
Invalid end_sector in partition table of  
No boot signature in partition table of  
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart. 
Try (hd0,0 ) :  EXT2:  NTFS4:  NTFS5:  NTFS5p:  FAT32:  FAT16:  FAT12:  non-MS: skip  Extended:  invalid or null  This partition is NTFS but with unknown boot record. Please
install Microsoft NTFS boot sectors to this partition correctly, or create an
FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there.                             hot-key        GRUª

---

### Post by yanceypd on 2009-10-15
I would make sure to defrag the Vista maybe a couple of times.  Then using the computer manager remove the extra partition.  Then run the live cd test.  If the disk tests ok try installing from live CD.  Works good for me.:)

---

### Post by Bondy on 2009-10-15
ok sorry for being lazy not read everything (got to go to bed very soon)

But Ive been trying to install ubuntu on a laptop tonight but it kept giving acpi errors so finally once Id tried the minimal install after the splash screen locking up I tried a text based install which is when I found the errors

an install got to the partioning but only gave me the option to format the drive completley so it could be because your telling the install to ignore certain errors if your setting paramaters

The laptop also had vista installed Id have wiped it if had of been my own but unfortunateley it wasnt

---

