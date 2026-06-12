---
title: "problem accessing a partition"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-21
Hi, I have recently installed ubuntu 10.04 and have the following setting in my computer

sda1              winxp          14GB
sda5              Debian          8GB
sda6               swap            1GB
sda7              /data             11GB   (ext 4 partition, common data location for both Debian and Ubuntu)
sda8              Ubuntu         8 GB
sda9              windows      37GB    (mounted on /media/windows)

So I have three operating systems installed in my computer - xp , debian and ubuntu. When I boot into ubuntu, before the login screen it says the following.

The disk drive for /media/windows is not ready yet or not present.
Continue to wait or press s to skip or m for manual recovery.

If I press s, it skips the thing and then gives me the login screen. After login, the places menu on top shows only sda1, sda5 and windows. Before this new installation of ubuntu, the places menu used to show the following which was quite convenient.

                    As it appears in the Places menu
                  -----------------------------------------
sda1       - 14GB Filesystem
sda5      -    8GB Filesystem
sda7        - 11 GB Filesystem
sda9     -     37GB filesystem

My questions are

1) I am not able to write to /data partition which is the common data partition for both debian and ubuntu. How to I make it writable. It has the following permission (drwxr_xr_x)
2) where did my /data link in places menu disappear. 
3) How does ubuntu know the name of the volume label in windows xp ( the volume label of sda9 was windows in my xp os) 
4) When I click the windows filesystem link in places menu it get mounted in /media/windows_ and not /media/windows ( the underscore is the difference, it basically creates a new directory). How do I fix this. I want it to be mounted in /media/windows when booting itself.

Please help. Thanks in advance

---

### Post by shai3421 on 2010-05-21
If you want to add /data to your Places list all you have to do is open the file explorer (Places -> Home Folder), and navigate to the parent folder of /data, then you drag data to the Places pane on the left side of the window (it should be there by default, if not press F9). You can also delete items from the pane to remove them from the Places panel.

---

### Post by efflandt on 2010-05-21
From a terminal, you may want to to make it 132 columns from the terminal menu, then copy and paste the output of **sudo fdisk -l** (small L), **cat /etc/fstab**, and **sudo blkid**.  After you paste that in the Message, highlight it and put code tags around it by clicking the **#** symbol at the top of the Message box.

Ubuntu usually uses UUID to identify partitions, unless you do something different.  Partitions mounted during boot need proper options in /etc/fstab.

I do have a problem with grub2 not being able to find or read partitions with the new partition alignment on one PC, but not partitions on a drive I successfully boot from not showing up in Places.  It is strange that it thinks that partitions on the drive you are booting from are not ready. If you type **dmesg | less** or look through /var/log/messages, is there any more info about that?

See: [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)

---

### Post by oaridus on 2010-05-22
The write problem with /data partition ----- is this due to the ntfs filesystem of the partition? Previously when I didn't have any problem to write, it was vfat32.

---

### Post by oaridus on 2010-05-25
> **oaridus said:**
> The write problem with /data partition ----- is this due to the ntfs filesystem of the partition? Previously when I didn't have any problem to write, it was vfat32.

My bad. I got confused with ntfs windows partition and /data partition which is ext4 file system. Now I have some good update news. I fixed the write problem by doing the following

sudo chown -R sid:sid /data. Now the permissions are drwxr_xr_x

Now the second problem of putting /data in the Places menu is interesting. If instead of mounting /dev/sda7 to /data I mount it to /media/data then it appears in the Places menu. This is what happens when you plug in a usb device. it opens in /media/New Volume. So to appear in Places menu mount the device in /media.

As for the third problem, it was I who gave it a name that /dev/sda9 should be mounted as /media/windows. So I guess the Places menu took the name windows from there. 

The last problem, I deleted the folder /media/windows and now the device /dev/sda9 when clicked mounts in /media/windows. 

But I still have the problem of getting the message at the beginning of the login screen that windows is not ready or the partition is not existing. Press s for skip.. etc etc... How do I Fix this..

---

