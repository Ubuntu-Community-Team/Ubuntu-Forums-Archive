---
title: "What is my Ubuntu-designated drive called and how do I do drive/sector repairs on it?"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by jnlwriter on 2010-07-23
Greetings:

I just installed Ubuntu 10.04. I started with a Dell Laptop, 320 GB, which I had partitioned into C and D, equally. C has MS Windows on it. D was blank. In the Ubuntu set up I allocated free space: 50 GB to / , 10 GB to swap and 40 GB to /home. (I am a major newbie, and not technically inclined. I only know how to look things up and follow directions, so don't assume any knowledge here please!)

I assumed Ubuntu was going to install on the empty D drive. But when I go to "My Computer" in MS word, I only see the C drive qith 100GB and the D drive with the 100GB, and whatever drive (partition) Linux is on, I don't see it here.

Why does this matter? Well, I don't really care if Ubuntu is invisible from MS Windows or not. BUT, there was an error in one of the sectors when I booted into Ubuntu. It worked, but had an imminent failure warning-bad sectors. I only know how to fix disk errors from a c prompt. So without knowing what to even call the drives Ubuntu is on... or how to access them, I'm at a dead end. 

I will go to the documentation and search for disk maintenance, restore, repair. But I'm also very curious why it doesn't show up in My Computer. I assumed that even with a different OS, I could "see" everything on my computer, but not so?

---

### Post by mapes12 on 2010-07-23
I guess you are looking for a dual boot configuration. This may help:-

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by matrixblue on 2010-07-23
It doesn't show up in Windows because Windows can't read Linux filesystems. Also Windows and Linux use different ways to view drives. Windows uses letters (C:, D:)

To repair the Linux disks you will have to run the File System Check (fsck) from an Ubuntu Live CD

Start the PC and boot from the CD. Select try Ubuntu without making any changes to my computer

When you are in the live environment open a terminal windows and type

**sudo fsck -A**

Linux is case sensitive so type it exactly as above. This will repair all your filesystems and you should be able to use Ubuntu normally.

---

### Post by migs73 on 2010-07-23
Hi there, don't assume any knowledge here either, but I might be able to explain why you can't see the partitions. Someone cleverer than me can help with the bad sectors.

The D partition you have in windows will contain all the linux stuff, but the partitions are formatted as EXT 3 or 4 and this is not visible to windows. On the other hand if you open up Ubuntu you will be able to see all the windows stuff as well as linux/Ubuntu can read NTFS and the FAT formatting used by MS.

As for the other stuff, I am sure you'll need to get your Ubuntu LiveCD out and wait for help.

Edit>

Matrix blue beat me to it and knows the other stuff, damn!! ;)

---

### Post by Mark Phelps on 2010-07-24
To get a look at your partitions, please open a terminal and enter "sudo fdisk -lu" (that's a lowecase L, not a one).

If you actually installed Ubuntu to "D", and "D" was formatted NTFS, then you did a Wubi install in which Ubuntu is installed to a file inside an MS Windows formatted partition.

If you created free space and formatted that into Linux partitions, then you have what we call a "traditional" dual-boot setup in which the OSs have their own individual partitions.

The fdisk command will show what you have done.

And, as others have said, since current Ubuntu versions use Ext4 as the default filesystems, MS Windows will NOT be able to see into the Linux files.

---

