---
title: "Partition/Grub question"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by 10up on 2009-09-22
Hey all.

Hopefully there is an easy solution to this that I am missing.

I've been using Ubuntu for a little over a year.  Great system, love it, never leaving.  Unfortunately I have to use CS4 for some work I do so I decided to make a Windows Partition.

I've successfully made the NTFS partition, successfully installed Windows, and solved my first problem of my computer wanting to always boot to Windows after I'd installed.

My problem now is that I cannot figure out how to make the windows partition show up in Grub.  I just have the several Ubuntu options.  

Any help would be greatly appreciated.

---

### Post by 10up on 2009-09-22
After looking in gparted it shows an error on the NTFS partition now as well.

I'm not really sure what the error would be as I, before reinstalling Grub via the livecd, had Windows and CS4 running perfectly on that partition.


Again, any and all help would be, well... helpful.

---

### Post by oldfred on 2009-09-22
You should see it on the left side pane of Naultius as the driver for ntfs partitions is loaded by default, now.

To make it permanent, you have to make a mount point and add a line to fstab.

sudo mkdir /mnt/windrv
 or to put it into your home
sudo mkdir ~/windrv
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

add a line like this with whatever name you used as  a mount point and the the correct ntfs partition.
/dev/sdaX /mnt/windrv ntfs relatime 0 2
or 
/dev/sdaX /home/[COLOR=DarkRed]login_id[/COLOR]/windrv ntfs relatime 0 2
  where [COLOR=DarkRed]login_id[/COLOR] is your name or where ~ is equal to  /home/yourname
sudo mount -a

sudo mount -a reloads the new fstab and will give error message if incorrect.

You can use sda or uuid or label as the drive id to see uuid or labels:

blkid -L

more info and examples:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubuntfs.html](http://ubuntu.swerdna.org/ubuntfs.html)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Darkwing-Duck on 2009-09-22
With redoing Grub to show the windows boot there is a good howto here.

[http://gwos.org/udsf/doku.php/core:grub:restore#configuring_grub_menu](http://gwos.org/udsf/doku.php/core:grub:restore#configuring_grub_menu)

Hope this helps you.

---

### Post by 10up on 2009-09-22
I actually don't see it on the side panel in nautilus.  It shows up in gparted.


I've done this twice now, I just can't figure out what I'm doing wrong...

---

### Post by 10up on 2009-09-22
Okay, I've decided to reformat the NTFS partition of the HDD and do a fresh install of XP on it.  

If anybody could tell me the steps to actually make this work correctly I would be forever grateful. 

Just in case it's helpful to anyone this is the output of fdisk -l



```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       28645   230090931   83  Linux
/dev/sda2   *       28646       37592    71866777+   7  HPFS/NTFS
/dev/sda3           37593       38913    10610932+   5  Extended
/dev/sda5           37593       38913    10610901   82  Linux swap / Solaris
```

Thanks in advance

---

### Post by kansasnoob on 2009-09-22
Well if you've already reformatted any info provided in now moot.

I'll be glad to help you but we must start with what exists now. Right now!

You can even PM me!

---

### Post by 10up on 2009-09-22
per your request here is a screenshot of gparted kansasnoob.


I really appreciate your help!

[IMG]http://i84.photobucket.com/albums/k31/10up64/Screenshot-3.png[/IMG]

---

### Post by kansasnoob on 2009-09-22
This guide is perfect for you:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by kansasnoob on 2009-09-22
I wish you hadn't got impatient and reformatted that win partition as the only thing remaining was to add win to grub!

Reformatting or deleting a partition goes fast!

Reinstalling goes slow!

---

### Post by 10up on 2009-09-22
very true!

I think after stumbling along the first 3 steps my brain went into hibernation.

That guide worked perfectly! If only everything were so simple.  Thanks a ton for your help.

---

