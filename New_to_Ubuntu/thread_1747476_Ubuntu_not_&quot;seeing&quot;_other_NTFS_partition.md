---
title: "Ubuntu not &quot;seeing&quot; other NTFS partitions (internal and external)"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-02
I have an external hard drive which is formated in NTFS as well as an NTFS partition which is next to my Ubuntu installation.  Ubuntu seems to be able to see the external drive in the USB port but offers no shortcut in Nautilus to mount it.  Likewise the Windows partition is displayed when I type "sudo fdisk -l", but it too is not shown in Nautilus as being available.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13944   112005148+   7  HPFS/NTFS
/dev/sda2           13945      121601   864754822    5  Extended
/dev/sda3           22455      120951   791177152+  83  Linux
/dev/sda5           13945       22454    68356543+  83  Linux
/dev/sda6          120952      121601     5221093+  82  Linux swap / Solaris

```

Any ideas what might be causing this?

---

### Post by wigout on 2011-05-02
You have 2175 posts as I reply to this vs my 29 so... take my advice heaping spoonfuls of salt.

I searched for:
Ubuntu not "seeing" other NTFS partitions

and came across this older thread where someone seemed to have the same problem:
[http://ubuntuforums.org/showthread.php?t=780842](http://ubuntuforums.org/showthread.php?t=780842)

and the person solved their problem by installing "psydm"
EDIT: changed psyadm to psydm, my error!
And have you tried mounting the partitions on the command line?

mkdir /home/user/Desktop/ntfs-test
sudo mount /dev/sda1 /home/user/Desktop/ntfs-test

and if so what error messages do you see?

Humbly offered,
wigout

---

### Post by diablo75 on 2011-05-04
> **wigout said:**
> You have 2175 posts as I reply to this vs my 29 so... take my advice heaping spoonfuls of salt.

I searched for:
Ubuntu not "seeing" other NTFS partitions

and came across this older thread where someone seemed to have the same problem:
[http://ubuntuforums.org/showthread.php?t=780842](http://ubuntuforums.org/showthread.php?t=780842)

and the person solved their problem by installing "psyadm"

And have you tried mounting the partitions on the command line?

mkdir /home/user/Desktop/ntfs-test
sudo mount /dev/sda1 /home/user/Desktop/ntfs-test

and if so what error messages do you see?

Humbly offered,
wigout

I can't seem to find a package called "psyadm" in Synaptic so I don't know where to get that package from.

I was able to manually mount any partition I wanted using the commands you outlined and no error messages occurred, but this thing used to do this automatically for all partitions, including the CD-ROM and any other USB flash drive I might insert would be auto-mounted.  I'd really like it to be that way once again.  Any idea what I need to do to make that happen?

---

### Post by oldfred on 2011-05-04
I prefer to manually edit fstab as the one time I tried one of the gui versions, I still had to edit it. Either way it is best to have some understanding of fstab, mounting, and the options available. and its PySDM.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Anytime you edit fstab, be sure to run mount -a to make sure there are no errors. It will just return if not errors or list problems. Some problem can prevent rebooting, so it is vital to resolve issues.

To see your UUID and partitions:
sudo blkid
sudo fdisk -l
cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
#Edit fstab first, with partitions & UUIDs of NTFS partitions

Examples from my fstab, I mount in /mnt so it does not automatically appear in Nautilus:
# Entry for /dev/sda1 :"
UUID=04B05B70B05B6768          /mnt/cdrive  ntfs-3g      defaults           0  0  
# Entry for /dev/sdc2 :"
UUID=44332FD360AA9657         /mnt/shared  ntfs-3g      defaults            0  0


# remount from updated fstab
sudo mount -a

---

### Post by wigout on 2011-05-04
it's psydm not psyadm sorry. I edited my original post.

---

### Post by diablo75 on 2011-05-04
> **oldfred said:**
> I prefer to manually edit fstab as the one time I tried one of the gui versions, I still had to edit it. Either way it is best to have some understanding of fstab, mounting, and the options available. and its PySDM.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Anytime you edit fstab, be sure to run mount -a to make sure there are no errors. It will just return if not errors or list problems. Some problem can prevent rebooting, so it is vital to resolve issues.

To see your UUID and partitions:
sudo blkid
sudo fdisk -l
cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
#Edit fstab first, with partitions & UUIDs of NTFS partitions

Examples from my fstab, I mount in /mnt so it does not automatically appear in Nautilus:
# Entry for /dev/sda1 :"
UUID=04B05B70B05B6768          /mnt/cdrive  ntfs-3g      defaults           0  0  
# Entry for /dev/sdc2 :"
UUID=44332FD360AA9657         /mnt/shared  ntfs-3g      defaults            0  0


# remount from updated fstab
sudo mount -a

Very helpful.  Thanks!

---

