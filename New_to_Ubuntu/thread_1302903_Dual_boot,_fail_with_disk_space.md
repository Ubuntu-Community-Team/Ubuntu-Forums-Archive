---
title: "Dual boot, fail with disk space"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by Patti0 on 2009-10-27
Hello, ived dual bootet my vista with ubuntu.
But when i want to install updates on ubuntu, it says that i dont have enough disk space.
This message will appear:

The upgrade needs a total of 483M free space on disk '/'. Please free at least an additional 340M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

And my labtop have 2 harddisk's with 70bg on both of them?

btw when i go on vista, i have 25gb left on C and 10gb on D.

Any idears ppl?

---

### Post by philinux on 2009-10-27
Open a terminal and run this.

```
df -h
```

Post back the output.

Apps>Accessories>terminal.

---

### Post by mapes12 on 2009-10-27
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by alphaniner on 2009-10-27
Boot into Ubuntu and open a terminal.  Post the output of

```
sudo fdisk -l
```

```
df -h
```

---

### Post by drs305 on 2009-10-27
Patti0,

Welcome to Ubuntu and the Ubuntu forums.

As you were advised (several times it appears ;-) ) run the "df -h" command. If it shows root / full, at only 2.5GB, you were a 'victim' of a bug in the Ubuntu installer. If you just installed Ubuntu and chose side-by-side with Windows, if you didn't move the slider the default installation is too small.

You have two options: Reinstall and change things in Step 4, or move some space from Windows (or another partition) into your Ubuntu partition. I've written help guides for both:

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

2.5GB  INSTALL
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If your partition is much larger and you wonder where your free space went, here is another guide:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Sorry your first exposure to Ubuntu is causing some problems, but we can help get you through this.

---

### Post by LewRockwell on 2009-10-27
covered...A to Z in ten minutes flat!

well-done comrades!

.

---

### Post by Patti0 on 2009-10-28
Thanks, but ived tried now.
Remeber im a beginner!

After doin the sudo fdisk -1 it says :

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

and after doin the df -h it says:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2,3G  2,2G   65M  98% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  108K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  168K 1006M   1% /dev
tmpfs                1007M  520K 1006M   1% /dev/shm
lrm                  1007M  2,4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             466G  441G   26G  95% /media/Pattio

I dont know what to do with this :(

---

### Post by drs305 on 2009-10-28
> **Patti0 said:**
> Thanks, but ived tried now.
Remeber im a beginner!

After doin the **[COLOR="Red"]sudo fdisk -1[/COLOR]** it says :


and after doin the df -h it says:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             **[COLOR="Red"]2,3G  2,2G   65M  98% /[/COLOR]**
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  108K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  168K 1006M   1% /dev
tmpfs                1007M  520K 1006M   1% /dev/shm
lrm                  1007M  2,4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             466G  441G   26G  95% /media/Pattio

I dont know what to do with this :(

The fdisk command switch is a lowercase L (sudo fdisk -l) - don't worry, it's a common mistake. 

The second command result confirms that Ubuntu installed itself on a 2.5GB partition. You will have to do one of the two things I mentioned in the earlier post. Read through them and decide which way to go. With your experience, reinstalling may be the easier options (make sure to move the slider in Step 4. I'd recommend at least 10GB for the partition size).

If you have questions, just ask. We were all newbies at some point.

---

### Post by Patti0 on 2009-10-29
I dont rly know how to uninstall ubuntu?

---

### Post by drs305 on 2009-10-29
> **Patti0 said:**
> I dont rly know how to uninstall ubuntu?

You don't really have to uninstall it. You can just install on top of the failed installation. But to make it more foolproof, do this:

Boot the LiveCD and choose the "Try without installing option".
At the Desktop: System, Administration, Gparted (or Partition Editor).
You will probably have 3 partitions: Windows, Ubuntu, and Ubuntu swap. If any have a "key" symbol next to them in the lower panel, it means they are mounted. Highlight that partition and then in the top menu, click on Partition, Unmount (or "swapoff" for the swap partition). 
Remove the Ubuntu and Swap partitions. Click on the partition, then > Partition, Delete Partition.

Once you have deleted the Ubuntu and swap partitions, reboot and reinstall Ubuntu. Do everything the same as before, but in Step 4 Partitioning, if you choose "side by side" with Windows, make sure you move the slider at the bottom to the left to make the Ubuntu partition at least 8GB (more would be better). Refer to the link in my previous post for the Howto: 2.5GB link. 

If you plan on storing personal data/files on the Ubuntu partition, make sure you add that amount of space in addition to the 8-10GB.

---

