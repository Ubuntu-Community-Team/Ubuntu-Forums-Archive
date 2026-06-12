---
title: "how to reinstall to increase ubuntu partition size"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by collards on 2009-11-28
Hello,

 I installed and double Booted Ubuntu beside Windows.  I am not able to receive updates because I do not have enough disk space in the 2.5G Ubuntu partition.   I believe i need to uninstall & reinstall Ubuntu with a larger partition.  what is the best way to do this?  

My disk is 18G total.  512MB RAM

Also if I do this, what effect will it have on the windows os? 

My windows is 98se which I will be dispose of soon. ...but I need Ubuntu now.

thank you

---

### Post by Exadrid on 2009-11-28
What can you do with win 98 that you cant do with ubuntu? I would understand if it was xp or further (not better) but 98? There's almost alway a alternate.

But if you have to keep it: Is the partition after or b4 windows in partition wise? and Do you have any space on windows left?

---

### Post by Buuntu on 2009-11-28
You can try enlarging your existing partition using gparted (System > Administration > GParrted) from your live CD if there is free space available right after the ubuntu partition (to the right of it in GParted).  Check out this guide: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by NoaHall on 2009-11-28
You can use the live cd to resize the partition without losing any data.

---

### Post by ajgreeny on 2009-11-28
Depending on how much disk space you have used in Win98, you may be able to shrink that partition with gparted, and increase the ubuntu partition size.  However,  18 GB is pretty small to use for a complete single install, never mind trying to dual boot, so I would seriously consider backing up the personal files you have on Win98, then installing Ubuntu on the whole disk, and then restoring the backed up files to your Ubuntu home.

I'm sure there can't be much you can do on Win98 that is not possible on Ubuntu in a much faster and more secure manner.

---

### Post by collards on 2009-11-28
Thanks everyone, 

 finances kept me limited to Windows 98 so I absolutely get your point and want to ditch it.  I still have some things to finish up using windows.  I haven't been able to figure out how to move some of my data and messages --that I need to keep for a little while --over to Ubuntu.

---

### Post by Buuntu on 2009-11-28
You're  looking too hard - to move data from Windows to Ubuntu (granted you are currently in Ubuntu) you can just drag and drop as long as the Windows partition is mounted to your filesystem (just click on the right partition under Places in the top left corner)

---

### Post by ajgreeny on 2009-11-28
Just copy them to a usb flash or hard disk, and then when you have got rid of win98, copy them back to your ubuntu home.  If you have no usb disks, burn them to a CD or DVD.  If you don't have a CD/DVD burner, then you need to get some way to backup your files, so beg or borrow a drive you can attach and use that.

If none of those are possible, I don't think you can go any further.

---

### Post by collards on 2009-11-28
Thanks all,  sorry for the delay in responding..everything is slow .probably because of low disk. 

 I can't get the terminal to open for me...maybe because I don't have the updates ???  but from the installation graphic,  it appeared that the disk is full.   Will gparted work with a full disk?    Ubuntu is installed on the right hand side. 

I am willing to remove what I can do without in Windows98-- that won't affect access to emai & contact data for now.

 I am going to look at the recommended links.  

How do I use the disk to partition?    

Sorry I am brand new at ubuntu.

---

### Post by arapa on 2009-11-28
1. Boot into Windows 98. 

[INDENT]1.a Move what you can off of your WIN 98 partition (as suggested move to a USB drive, burn to a CD-R, delete junk etc).[/INDENT]

[INDENT]1.b Defragment your Win 98 drive[/INDENT]

[INDENT]1.c Take note of how much space is being used by your Win 98 installation.[/INDENT]

2. Boot off of the Ubuntu Live CD (Do not click on (mount) any drives).

[INDENT]2.a Read [Resizing Partitions]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition")[/INDENT]

If you get stuck - just ask.

---

### Post by collards on 2009-12-01
Hello & thanks again to all previous advice, which has been so helpful. 

Here's where i am--

I installed Ubuntu onto a drive that had Windows OS -- and most of the Windows partition was unused space.  I have backed up my data files & got rid of unneeded stuff.

After carefully reading & re-reading "Ubuntu documentation & GParted help I used GParted to resize  (shrink)  the windows partition to create the necessary unallocated space --so that I could  increase Ubuntu size to 12G--which I read is a good amount. 

but after retrying numerous times I am not able to resize Ubuntu into the now unallocated space.

Ubuntu & LInux-swap are both logical partitions inside Extended partition.  Status for Linux-swap is active and mounted  & status for Extended is busy---probably because of Linux (???)  so the resized button remains greyed out.  

Here are the details:                                                                 
Windows /dev/sda1        5.86 G

Unallocated                 10.29G

_Extended_ /dev/sda         2.50 G

    Ubuntu /dev/sda5       2.33 G

    Linux-swap /dev/sda6 172.54 M


My questions:

Is is possible to resize this Extended partition?  Is Linux-swap busy because I am using the Live CD? 

Do I uninstall & reinstall in the now larger space? or do I delete the Extended partition?

If I am overdoing this, i apologize.  i just want to be clear.

thank you,

Collards

---

