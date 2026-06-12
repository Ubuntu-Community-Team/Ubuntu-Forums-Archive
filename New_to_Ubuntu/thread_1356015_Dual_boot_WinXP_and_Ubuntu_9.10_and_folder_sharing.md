---
title: "Dual boot WinXP and Ubuntu 9.10 and folder sharing"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Nermi on 2009-12-15
If I dual boot XP and Ubuntu 9.10 (installed on the same drive or separate drives), can I access my XP files while I am in Ubuntu, and vice versa? My first thought would be, I can't because the other operating system is not booted... 

Or... ?

---

### Post by Ducatiboy Stu on 2009-12-15
Yes... Ubuntu will show your Win XP  partition as a seperate drive, that you can browse with Nautilus etc. You can easly copy/delete files in your windows partition from ubuntu

For windows, you will need to install Ext2IFS for windows

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

This allows windows to read/write into your ubuntu partition. without ext2ifs, windows will show your ubuntu partition as an unknown file system.

---

### Post by Jerry N on 2009-12-15
It was my impression that Ext2IFS does not work for EXT4, which is the default file system for Ubuntu 9.10.  Is that not still the situation?  In any case, Ubuntu will read (and write, so be careful) to the Windows NTFS partition without difficulty.

---

### Post by teward on 2009-12-15
I'm going to contest the "NTFS will work with Ubuntu" statement, because in certain instances, the Ubuntu install will not recognize the Windows partition.  This seems to happen on IDE drives hooked up to my computers, and I've seen it happen before on other computers with IDE hard drives.

Assuming your computer is fairly new, you shouldn't have a problem because they use SATA instead of IDE.

---

### Post by northern lights on 2009-12-15
> **Ducatiboy Stu said:**
> For windows, you will need to install Ext2IFS for windows

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

This allows windows to read/write into your ubuntu partition. without ext2ifs, windows will show your ubuntu partition as an unknown file system.
ext2ifs still doesn't support ext3 journaling and no, it hasn't caught up with ext4 yet. So if you're on a default Karmic install, that won't help.

Personally, I wouldn't want a Redmond OS to be able to write to (and hence possibly destroy) my Linux filesystem. So I'd suggest creating a FAT32 formatted shared partition.

---

### Post by sandyd on 2009-12-15
> **Jerry N said:**
> It was my impression that Ext2IFS does not work for EXT4, which is the default file system for Ubuntu 9.10.  Is that not still the situation?  In any case, Ubuntu will read (and write, so be careful) to the Windows NTFS partition without difficulty.
nope. no support for ext4 -yet

---

### Post by sandyd on 2009-12-15
> **Nermi said:**
> If I dual boot XP and Ubuntu 9.10 (installed on the same drive or separate drives), can I access my XP files while I am in Ubuntu, and vice versa? My first thought would be, I can't because the other operating system is not booted... 

Or... ?
i simply advise you to create the partition table like this
(in any order you want)
[recovery] (some computers may have this
[NTFS volume for sharing] (use FSTAB to mount at boot)
[windows]
[linux]
[linux swap]

as some of the posters above said, dont let windows have access to the linux partition.
i learned the hard way when norton/mcafee (or something else, cant remember) removed my grub installation and said it was a boot sector virus.

---

### Post by Ducatiboy Stu on 2009-12-15
I have had no problems with Ext2ifs reading ext3, I use it a lot to move files between NTFS and EXT3

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
I have Ubuntu on a partition on my IDE drive and Win 7 on my SATA drive and have no problem accessing anything in my Win 7 install from Ubuntu.

---

### Post by Jerry N on 2009-12-15
I have had no problem at all in getting Ubuntu to read and write to NTFS partitions on an IDE drive.  My test computer has no SATA drives, only IDE.

Jerry

---

### Post by Ducatiboy Stu on 2009-12-16
Can confirm that ext2ifs in XP cannot read Ubuntu 9.10 ( EXT4 )

Works fine with Hardy ( 8.04 ) which is formated to Ext3...

Grrr....what a PITA   :(

---

### Post by Nermi on 2009-12-16
So, basically, when I install Ubuntu as dual boot with XP, I WILL be able to access my Windows files, meaning open, edit and save the changes, and I MIGHT be able to access my Ubuntu files from XP (depending on my luck, my hardware, and direction of the wind? :))

OK, now does this all apply when I install Ubuntu on separate drive instead on separate partition?

And how about a printer that is connected to my XP? Will I be able to use it? 

If I make this work, I will switch to Ubuntu for all my work and only access existing XP files that need to be edited from time to time...

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
As I said, in my machine  win 7 is on the first partition of a SATA drive and Ubuntu is on the first partition of an IDE drive, and I've had no probs. As for the printer, it'll depend on drivers.

---

### Post by Nermi on 2009-12-16
Well, my printer works on my XP and my Ubuntu (as they are different machines now), so I guess my printer SHOULD work, as far as drivers are concerned?

The only reason I want to put both Ubuntu and XP on the same machine is that my Ubuntu one is little slow (older system). Plus, I don't like to have two monitors, two mice... etc, and no the SWITCH hardware didn't work the way I expected. 

Thank you all for all your help. I will try and post results back here.

---

### Post by rsgangr on 2009-12-22
Hi Nermi,
I have successfully been dual-booting Windows XP and Ubuntu 8.04, installed on separate drives, for about a year now. I can print from both operating systems (HP OfficeJet 6213) and I am able to access all XP partitions from Ubuntu, whether FAT32 or NTFS. However, I recently found that the XP c: partition will not be accessible if the Windows shutdown was faulty. This discovery followed a sad episode of 8 consecutive XP crashes, but that's another story!

Hi Carlee,
I completely agree with your advice never to allow Windows access to a Linux partition.

---

### Post by colinmccubbin on 2010-01-26
I can confirm that Ext2IFS doesn't work with 9.10.](*,)

Yesterday I loaded a new 'box' with win xp and 9.10, and as I had done with a similar 8.04 installation in the past I downloaded and installed Ext2IFS_1_11a.exe  under windows, and set the Ubuntu partition to be L:

Open Windows explorer, see a drive :L, but on clicking I get the "The disk in drive X: is not formatted. Do you want to format it now?"  message.. NOPE!:eek:

Downloaded mountdiag.exe  from fs-driver.org and ran it in a Windows command console.

The resulting message from mountdiag L:      is: 

[I]"The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not mount it because there is at least one incompat feature flag set.  The Ext2 IFS software does not implement:
*extents*
The Ext2 IFS 1.11 software does not implement this feature, and sio it is not able to access such Ext2/Ext3 volumes.
*unknown imcompat feature bit 0x00000200 *
The Ext2 IFS 1.11 software does not implement this feature, and sio it is not able to access such Ext2/Ext3 volumes.
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not mount it because the file system has an inode size unequal to 128 bytes.<inode size: 256 bytes>.

The only way to solve this is to back up the volume's files and format the file system: give the mkfs.ext3 utility the -I 128 switch. Finally restore all the backed up files..."[/I]

I emailed the author of Ext2 IFS who hasn't replied, I suspect he/she is well aware of the problem. I haven't tried the 'fix' that mountdiag suggests, I'll just set up a ntfs partition for now..  I'd never considered that windoze might cr*p on my Ubuntu files so perhaps that is a good reason to not use Ext2IFS anyway. Thanks for the advice..

---

### Post by hhlp on 2010-01-26
the system disk default in karmic is ext4 and Ext2IFS doesn't support  this type of file yet

---

### Post by J V on 2010-01-26
Sharing home with windows

It is possible to share your home folder with windows.

Linux shortcuts (known as symlinks) act just like folders, so if a shortcut is at ~/shorty leading to ~/randomfolder/ which contains test.txt, you can also access it with ~/shorty/test.txt

Now, while windows has difficulty (At best) with accessing the Linux file system, you can still share your documents.

By replacing standard folders like ~/Pictures with symlinks to "/media/windowsdrive/Users/<yourname>/My Pictures" etc, all files saved to pictures, will actually be saved to the windows drive, meaning you can access and modify your stuff from both windows and Linux.

There are several things you should know before trying this:
• On windows, unless you specifically choose to encrypt something, it won't be encrypted, so an encrypted home will do you no good if you use this technique. You can however create an encrypted private directory to store your more sensitive data, while the rest is freely available to both operating systems
• Settings for some programs can also be linked, Firefox settings are similar on both OSs for example, so you could link your ~/.mozilla folder to the similar location on your windows drive. Again, your data won't be encrypted, so you should be wary of this if you save passwords
• If you are trying to share your home between two Linux OSs, it becomes much easier. All you have to do is put your home on a separate partition, which can be used for multiple OSs, and will make fresh installs much much easier.

---

### Post by colinmccubbin on 2010-01-27
I had a reply from Stephan Schreiber, author of Ext2 IFS....
 
[I]
Hello,
Ext2 IFS is not able to mount your volumes because they are Ext4.

Ext4 support is being developed but I can't promise that the next version of Ext2 IFS will have all features of Ext4.

Kind regards
Stephan Schreiber[/I]

---

