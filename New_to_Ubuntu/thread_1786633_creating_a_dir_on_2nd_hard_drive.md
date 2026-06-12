---
title: "creating a dir on 2nd hard drive?"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by KwaggarookDagga on 2011-06-19
I have installed a 2nd hard drive into my Linux box. Created a partition. Formatted the partition to .ext4. But would like to create a dir on this partition so I can mount this 2nd partition. But I don't know how????

---

### Post by jtarin on 2011-06-19
Open nautilus File manager and look to the file tree on the left and see if your drive is mounted, if it is, then click on it to open it and then right click to make a new dir/folder.

---

### Post by KwaggarookDagga on 2011-06-19
I can now see the drive in the file manager. But can't create a dir as it is greyed out. I would also know how to do this from the command line

---

### Post by jtarin on 2011-06-19
From the command prompt cd (change directory to the directory where you will make a new one. Example....I have an external drive partitioned into 3 partitions. One partition is named "Home" (without quotes)to change into it and create a directory I would....```
username@localhost$ cd /Home
```
then press enter....then my prompt should show I am in the /Home dir. Once in the directory I would issue the command ```
mkdir <somename>
```....done.

---

### Post by KwaggarookDagga on 2011-06-19
cd home would only take me to the hard drive on which Linux is installed on..... I need to get to this 2nd drive first(or access) and then create this "home" dir in your case on the 2 hard drive.

if I go cd/ dev/sda2 it tell it isn't a dir and rightly so

---

### Post by dFlyer on 2011-06-19
Use disk utilities and mount the drive. That way it will not be grayed out. You can then use Nautilus or the command line to create the directory. Are you dual booting by any chance with windows? If so windows will not be able to read your ext4 formated partition.

---

### Post by KwaggarookDagga on 2011-06-19
I navigated to the media dir,found the 2nd hard drive called a7d24blah blah blah accessed the drive from there and created the dir in there. But still can't create the mount point to the newly created dir

---

### Post by DawieS on 2011-06-20
The drive is probably greyed out due to the owner being "root" and you not having write permissions. To correct this, type in a terminal:
```
sudo nautilus
```This will open a file browser owned by "root". Click on the drive to mount it, then right click on the drive icon and select "Properties" then "Permissions".

I recommend that you change both the "Owner" and "Group" to your user name, with "Create and delete files" at "Folder access", and "---" at "File access". At "Others" you may select "Access files" with "---" at "File access", or whatever permissions you may deem appropriate.

Click on "Apply Permissions to Enclosed Files" and close the file browser and terminal.

You can also give your partitions meaningful labels by using "System - Administration - Disk Utility". Click on the partition, then "Edit Filesystem Label".:grin:

---

### Post by oldfred on 2011-06-20
You can do it from command line. But if it is a NTFS partition you cannot change permissions, they are set at mount.

sudo mkdir /data
sudo mount /dev/sda5 /data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
sudo chmod -R 777 /data
sudo chown -R $USER:$USER /data
#where $USER should be your login name
#or to see user
echo $USER

If it is a permanently mounted drive you many want to have it mounted when you reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

