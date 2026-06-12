---
title: "want remove a duplicate ubuntu"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by denisscott on 2010-12-19
I had a problem with ubuntu 10.04 so I reinstalled it and now Ihave got two lots booting along side vista how can i remove one version of ubuntu without messing it all up, tks;)

---

### Post by KdotJ on 2010-12-19
Hey, did your reinstall overwite your old one? Or did you reinstall it to a different partition/disk?

If your reinstallment over the top of your previous Ubuntu, then these aren't duplicate Ubuntu's, they are different kernel versions. If you check the numbers after it says....

"Ubuntu, with Linux xxxxxxxxx"

(the x's representing version number), you'll see that they are different. These are perfectly normal, and I'd just advise you to leave them there. Basically, when you get a new kernel in the updates, Ubuntu will install it along side your existing kernel. You can then choose which kernel to boot into from the menu you're referring to.

---

### Post by cgroza on 2010-12-19
You mean you have 2 Ubuntu installs on the hard drive and you wish to remove one?

---

### Post by Rubi1200 on 2010-12-19
I suggest you post the output of ```
sudo fdisk -lu
``` so we can get a better idea of what is going on.

Go to Applications > Accessories > Terminal and copy/paste the command and output.

Thanks.

---

### Post by denisscott on 2010-12-19
hi
it is as followsenis@denis-laptop:~$ sudo fdisk -lu
[sudo] password for denis: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe78ae78a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   118304776    59152357    7  HPFS/NTFS
/dev/sda2       219945915   234436544     7245315    7  HPFS/NTFS
/dev/sda3       118306814   219945914    50819550+   5  Extended
/dev/sda5       151364493   217038149    32836828+  83  Linux
/dev/sda6       217038213   219945914     1453851   82  Linux swap / Solaris
/dev/sda7       118306816   149886975    15790080   83  Linux
/dev/sda8       149889024   151363583      737280   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by sandyd on 2010-12-19
> **denisscott said:**
> hi
it is as followsenis@denis-laptop:~$ sudo fdisk -lu
[sudo] password for denis: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe78ae78a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   118304776    59152357    7  HPFS/NTFS
/dev/sda2       219945915   234436544     7245315    7  HPFS/NTFS
/dev/sda3       118306814   219945914    50819550+   5  Extended
/dev/sda5       151364493   217038149    32836828+  83  Linux
/dev/sda6       217038213   219945914     1453851   82  Linux swap / Solaris
/dev/sda7       118306816   149886975    15790080   83  Linux
/dev/sda8       149889024   151363583      737280   82  Linux swap / Solaris

Partition table entries are not in disk order
Nice. their all in an extended partition.

Post the output of 
```

sudo mount -l
```so that we can tell which one your actually running

---

### Post by JC Cheloven on 2010-12-19
My 2p:
Probably your last, 'good', install lies in /dev/sda7, but it really doesn't matter if it's in /dev/sda5 : deleting either partition (and eventually dsa6 swap) and expanding the other one will take more time than a fresh install, and will be more prone to errors. You could consider booting from live, saving your data if any, erasing partitions sda5 to sda7 using gparted, and fresh installing in the freed space.

---

### Post by denisscott on 2010-12-20
hi,enis@denis-laptop:~$ sudo mount -l
[sudo] password for denis: 
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/denis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=denis)
denis@denis-laptop:~$

---

### Post by Elfy on 2010-12-20
This is the one you are using 

/dev/sda7 on / 

Check swap while still running your new install - 

You might have both swap partitions listed in your fstab - check that while still in your install

```
cat /etc/fstab |grep swap
```

It might give you sda6 and sda8 - you can remove one of those as well - sda6 will be easiest.

Edit the file as root

```
gksudo gedit /etc/swap
```

Swap line will look _similar_ to 

> # swap was on /dev/sda5 during installation
UUID=66f8bf6a-aaac-471e-894b-cdb498691e64 none swap sw 0 0

Once you've checked swaps.

You can boot with the livecd - there's a partition editor in the sys admin menu 

Use that to remove the other one on /dev/sda5 and any not needed swap.

You should also be able to resize the new install with the unallocated space if you wish

---

### Post by denisscott on 2010-12-21
Hi Thanks to all I used the live cd and then used gparted to removed all the partitions and reinstalled using the live cd, no problems at all again may thanks
:popcorn:

---

### Post by Rubi1200 on 2010-12-21
Glad you got it sorted out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

