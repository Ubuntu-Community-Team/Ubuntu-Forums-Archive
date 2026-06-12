---
title: "Home Directory on VFAT/Fat32"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by kcampbe on 2009-12-04
Hello!

I have Karmic Koala installed and have my home directory located on a VFAT/Fat32 partition so that I can access my Thunderbird mail and other files from Ubuntu and Windows 7. ( I know, I know).

Anyway..  All of my files and directories have RWX permission.  This seems to cause an issue with my .ICEauthority file, which causes an error each time I boot.

I'm not able to remove the X permission from any file.

/etc/fstab contains this line:

/dev/sda4 /home vfat rw, exec, uid=1000, gid=1000, auto 0 0

Any thoughts on what I've done wrong and how I can change my mount line to allow me to remove X permissions?

Thanks - Kevin

---

### Post by DGortze380 on 2009-12-04
> **kcampbe said:**
> Hello!

I have Karmic Koala installed and have my home directory located on a VFAT/Fat32 partition so that I can access my Thunderbird mail and other files from Ubuntu and Windblows. ( I know, I know).

Anyway..  All of my files and directories have RWX permission.  This seems to cause an issue with my .ICEauthority file, which causes an error each time I boot.

I'm not able to remove the X permission from any file.

/etc/fstab contains this line:

/dev/sda4 /home vfat rw, exec, uid=1000, gid=1000, auto 0 0

Any thoughts on what I've done wrong and how I can change my mount line to allow me to remove X permissions?

Thanks - Kevin

FAT32 doesn't support Linux style permissions. I suggest finding an alternate solution. (perhaps mirroring your .mozilla directory to a fat32 partition?)

---

### Post by Merk42 on 2009-12-04
> **DGortze380 said:**
> FAT32 doesn't support Linux style permissions. I suggest finding an alternate solution. (perhaps mirroring your .mozilla directory to a fat32 partition?)

Or just using ext3 or 4 which you should be able to mount in Windows with [Ext2 Installable File System](http://www.fs-driver.org/) (yes you can mount ext3 and 4 even though it says 2)

I'd also suggest not saying Windblows, as that just sounds immature, but that's not at all what the topic is about.

---

### Post by kcampbe on 2009-12-05
Thank you for your feedback.

I've tried EXTFS2 but it doesn't seem to work on Windows 7.

How would I go about mirroring my Thunderbird/Mozilla directory/data?

Thanks again!

---

### Post by oldfred on 2009-12-05
If you boot both windows and Ubuntu often you can have the same firefox and thunderbird data in a common partition.
I created a FAT32 partition (before NTFS linux driver wrote reliably) 2-3 years ago and moved both firefox and thunderbird to the shared partition. I then edited the profiles in windows and linux to look the the common partition rather than the local one. It still worked even when I converted from Firefox version 2 to 3 and 3.5 on both windows & ubuntu. 

[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)
More info:
    *  (Firefox) ./firefox -profilemanager
    * (Mozilla Suite) ./mozilla -profilemanager
    * (SeaMonkey) ./seamonkey -profilemanager
    * (Thunderbird) ./thunderbird -profilemanager 
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by kcampbe on 2009-12-05
Thank you all!

Your great ideas have solved my issue.

Kevin

---

