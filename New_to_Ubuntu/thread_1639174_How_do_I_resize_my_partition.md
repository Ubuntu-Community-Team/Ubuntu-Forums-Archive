---
title: "How do I resize my partition?"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by ShadowVegan on 2010-12-06
I currently have one partition (Ubuntu 10.04) taking up my entire HDD. According to GParted my partitions are (file system in parenthesis):
unallocated (unallocated) 1.00MiB
/dev/sda1 (ext4) 289.44 GiB
/dev/sda2 (extended) 8.65 GiB
/dev/sda5 (linux-swap) 8.65GiB

/dev/sda5 seems to be within /dev/sda2

I like Ubuntu and want to keep it but for several reasons I also want a Windows partition. I have the Vista recovery disk that came with my laptop, I just need to make a partition. How do I shrink my Ubuntu partition (without deleting it or losing any files or software)? And how much space should I allow for each partition?

On my Windows partition I will have about 10GB taken up with software/programs, along with the obvious space that the OS itself takes up. I will be using Ubuntu for most things but no big programs. Currently according to GParted I am using 8.64GiB (in sda2... everything else is empty) and according to Disk Usage Analyzer I am using 4.1GB out of 284.9GB.

I'm very new to Ubuntu, I've been using it for only a few weeks, so don't expect me to know how to do much yet.

Thanks for any help.

---

### Post by Quackers on 2010-12-06
The best way to resize your Ubuntu partition is to boot from the Live cd and select "try ubuntu". Then when the desktop has loaded start up gparted and when it has scanned the disk right-click on the swap partition and select swapoff (may not be necessary on the live cd but better to be safe).
Then you can resize your main partition in a couple of ways. Using the tools at the top or by dragging the right end of the partition to the left. Don't forget to apply the changes by clicking on the arrow in the toolbar.

A word of warning though!
If you use the Vista recovery discs that came from your pc it is likely that they will want to default to using the whole hard drive to re-install Windows. You may or may not get the option to change it. Such a re-installation will also break grub, which will need to be re-installed.

---

### Post by ezsit on 2010-12-06
If your recovery disc works like most, it will wipe the entire hard drive and reinstall Windows to the factory setup. You will wind up wiping out Ubuntu. 

After you reinstall Windows, use the Windows Disk Manager to shrink the Windows partition to make room for Ubuntu. Run chkdsk a couple of times after you shrink the Windows partition before installing Ubuntu.

It is always better to install Ubuntu AFTER Windows is already on the hard drive since the Ubuntu installer will locate Windows and create the necessary multi-boot setup during installation. Installing Windows after Ubuntu will wipe the boot loader and make it necessary to reinstall grub to be able to boot Ubuntu again.

---

### Post by venicequeen7706 on 2010-12-06
before you do this, backup your system in case the computer crashes or something while resizing. I had this happen once and had to reinstall ubuntu.

You won't be able to resize a partition ubuntu is using at the moment, so you probably will have to boot from a live cd to do this.

go to System > Administration > GParted Partition Editor, if you don't have it install it through synaptic. 

click on the /dev/sda1 go to right click on it and select resize/move and make it the size you want. I would say since you have so much space on your hard drive make the partition about half its current size.

Then you will have to right click on the unallocated part which should be over a hundred GiB and select new. make that however much space is left on your hard drive. If you want to install windows I thing you want to change the drop down menu where is says file system to fat32, but I'm not positive because I don't really remember how to deal with windows file systems.

Hope that helps

---

### Post by ShadowVegan on 2010-12-06
Thanks for the replies. In that case I will probably wipe my HDD and then install Vista, then reinstall Ubuntu. Is there any way to save my GPG key? (I am using Thunderbird with Enigmail) Thanks.

---

### Post by oldfred on 2010-12-06
You want to back up /home as all your user data and user settings are in /home (including all your emails in a hidden .mozilla-thunderbird folder).

If you have done any system wide settings you may want to backup /etc. But if upgrading to a new version do not just copy it back. New versions may need different system settings or not.

If you have installed a lot of additional apps you can back up the list to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

---

### Post by aphatak on 2010-12-06
Oh, and remember that Windows wants to be in the first physical partition on the hard disk.

---

### Post by amjjawad on 2010-12-06
> **aphatak said:**
> Oh, and remember that Windows wants to be in the first physical partition on the hard disk.

The first **Primary** Partition ;)

---

### Post by ShadowVegan on 2010-12-06
Thanks for the replies.

> **oldfred said:**
> You want to back up /home as all your user data and user settings are in /home (including all your emails in a hidden .mozilla-thunderbird folder).
Can I just save it to a USB drive? After re-installing Ubuntu, do I just click and drag to overwrite the new home with the old home? And should I do the whole home folder, or just my user account (places --> home folder)? (my user account is the only visible file in home, I don't know how to find hidden files in Ubuntu)

---

### Post by oldfred on 2010-12-06
To see hidden files you click on view and choose show hidden files. You want the entire /home folder of your user.

If you copy to a USB drive it needs to be ext2 or ext3 formated. FAT does not recognize ownership and permissions and you will lose them. They can be reset but it creates complications.

It would be just like moving /home:

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

---

