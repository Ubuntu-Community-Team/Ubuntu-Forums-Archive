---
title: "Change partition mount point"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by KingLewy on 2011-06-14
Hi, I had problems with 11.04 so I decided to back up all my stuff and reinstall. I was given the option to install over the existing Ubuntu install and next to Windows 7, which suited me just dandy. The first time I installed I went to the effort of preparing 22GB logical partition mounted at / a 9GB Swap Area and a 125GB logical partition mounted at /home. After the second install I am left with an 18GB mounted at / two Swap Areas (one 4.2GB, the other the 9GB like I'd done before) and a 125GB logical partition that still contains all of my files, which is neat, but it just mounts like any other external device or partition and I can't figure out how to get it to mount permanently as /home. Any ideas? I'd be most grateful.  :)

---

### Post by trozamon on 2011-06-14
Open a terminal and type:

sudo gedit /etc/fstab

Then, you'll have to do a bit of looking for the line containing the 125GB part, then change the mount point. If that sounds intimidating, you can post that file here and I'll tell you what changes to make.

---

### Post by nzjethro on 2011-06-14
The line you add should be along  the lines of

```
/dev/sda4 /media/ ntfs defaults 0 0
```

I'm mounting sda4 (my media drive) to /media, to where I've set up shortcuts from /home.

The bits you should change to your situation are "/dev/sda4" (to your /home partition) and your mount point "/media/" (most likely to /home).

---

### Post by KingLewy on 2011-06-15
Thanks very much. Terminal gave me this:

(gedit:7219): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VK56WV': No such file or directory

(gedit:7219): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

and the fstab was this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=8e4d565e-6c5d-4ffe-8b1f-ace101994e65 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c923a91c-5c93-43dc-898c-5ee1fdbb96f3 none            swap    sw              0       0

I'm just confused :s

P.s.- sda4 is the whole 156GB Extended partition, sda5 is the 9GB Swap Space I set up with the first install, sda6 is the 125GB partion I want (and used to have) as \home, sda7 is the 18GB partition for \ (was resized to make new Swap Space, don't know why) and sda8 is the new 4.2GB Swap Space.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
> **nzjethro said:**
> The line you add should be along  the lines of

```
/dev/sda4 /media/ ntfs defaults 0 0
```I'm mounting sda4 (my media drive) to /media, to where I've set up shortcuts from /home.

The bits you should change to your situation are "/dev/sda4" (to your /home partition) and your mount point "/media/" (most likely to /home).
i belive yuo should di like this that may cause usses with flash drives
terminal
sudo mkdir /media/windows
fstab
/dev/sda6 /media/windows ntfs defaults 0 0

if you don't want it showing up on your desktop use mnt instead of media

---

### Post by oldfred on 2011-06-15
When you did your new install you must have used an auto reinstall and it just installed side by side wtih existing installs. Normal installs are just root & swap.
If you want to reuse existing partitions & existing /home you have to use manual install and choose which partition is / (root) & /home, it then finds existing swap.

You could reinstall and delete second swap, and resize your root to the original size and mount the /home as part of the install. Or you can mount your /home into your new install, but that will not house clean the duplicate swaps and other issues.

To mount your /home into your new install you just need to do the last part of a move /home. You in effect have already copied /home to a new partition, so you just need to edit fstab.

Three essentially identical move /home instructions. Look at last steps on adding /home partition to fstab. Choose one that makes more sense to you.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by KingLewy on 2011-06-15
The auto reinstall option took the place of the normal side by side installation, yes that's what I did. I thought it would be easier than the manual install.  I assumed that it would just re-use the partitions that I had already set up in the same way. Would an easy solution here be to simply reinstall again and do a manual install this time? I won't be losing anything. I only did this a couple of days ago.

---

### Post by trozamon on 2011-06-15
Reinstalling and doing a manual install will allow you to reuse partitions

---

### Post by oldfred on 2011-06-16
I agree with trozamon, that a manual reinstall (Something Else) would probably be best.

You may want to use gparted and edit partitions before the install, although you can do most of it as part of the install.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by KingLewy on 2011-06-19
I'm going to go ahead and reinstall. Thanks all who posted for your help.

---

### Post by KingLewy on 2011-06-19
.

---

