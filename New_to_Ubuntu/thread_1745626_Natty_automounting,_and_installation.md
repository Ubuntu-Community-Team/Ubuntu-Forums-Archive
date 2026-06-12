---
title: "Natty automounting, and installation"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Zerberus on 2011-05-01
Hello there,

Well I have been using ubuntu for a couple of months now, and I have a question in regards to automounting. But I also had a question why Natty didn't allow me to specify a personal location for my partition to be mounted.


Ok here I start.

So I have a acer netbook that I am really fond of, It has 120gb hard disk, 25 gb for my ubuntu, and 95 for whatever backup and files I use for my daily task.

Initially when I installed maverick, I was able to enter the location for my partition to be mounted at start-up. I like to be practical and I always mounted my partion as my desktop, thus whenever I download or work or do anything on my desktop it is always saved in my 95gb hard disk. 

thus the mount point would be 

/home/username/desktop

I find this the best and most efficient way of using two partitions.

However during installion of natty, I was not able to edit the location itself, I was only able to choose between the different prefixed drop-down menu, thus I didn't choose any location for mounting during installation. 

After my installation I installed mountmanager & pysdm, and specified that they should mount my 95gb partition on desktop. 

The mounting does happen, I am satisfied that I am able to see all my files, however the problem is, that the partition is not automounting, and that I am not able to edit/delete/remove/relocate any files, I can open folders and open files but that is about it.

Thus two things that I need, how to tell fstab to automount, and how to make my 95gb partition writeable.

my fstab file is as follows:

proc                                       /proc                   proc  nodev,noexec,nosuid  0  0  
UUID=ae7741d5-2361-44ac-8ba8-1b6dad6025ad  /                       ext4  errors=remount-ro    0  1  
UUID=c00ae2bd-f572-4447-baa7-a89a5eb296a7  none                    swap  sw                   0  0  
/dev/sda2                                  /home/zerberus/Desktop  ext4  defaults             0  0

---

### Post by gandaran on 2011-05-01
> However during installion of natty, I was not able to edit the location itself, I was only able to choose between the different prefixed drop-down menu, thus I didn't choose any location for mounting during installation. 
can still be done just like before natty, on older versions of ubuntu you choose the manual install but on natty its something else, I have done it yesterday but I cant remember exactly what option I used I think it was the last one.

---

### Post by powerpleb on 2011-05-01
The first thing I'd look at if I were you would be the permissions. Have you changed your username or something like that?

Try running "sudo chown -rv username ~/Desktop" and see if it you can read/write. This will set the owner of that directory and its contents.

P.S. I do similar things with my home folder, but instead of mounting partitions directly into the home folder, I mount them in the /mnt folder and run a symlink to my home folder. Eg. "ln -s /mnt/harddisk ~/Desktop". For me, I find it a bit better organised that way, especially when multiple users are using the same drive.

---

### Post by coffeecat on 2011-05-01
There was a bug that manifested just before final release - hence no time to fix it - that prevented you from typing in a custom mount point in the manual/advanced option, or whatever it's called now. Bug here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

Fwiw and for future reference, the workaround is to boot into the live desktop rather than go straight to the installer. Open gedit, type in your mountpoint and copy it into the clipboard with ctrl-C. Don't close gedit. Now start the installer and when you get to where you want to specify a mountpoint, right-click on the field and paste what's in the clipboard. You have to right-click to choose paste from the context menu, not left-click and ctrl-V - that doesn't work.

Anyway...

First comment: I think mounting a partition to the desktop is not advisable. I've never tried it - I don't think I ever will. A custom folder in home might be better. Whatever, so long as your 96GB is on sda2 then your fstab looks OK. So let's investigate. Post the output of these terminal commands:

```
sudo fdisk -lu
sudo blkid
mount
```**Please** post the output between [noparse]```
 and 
```[/noparse] tags for clarity. You will lose essential formatting if you don't.

---

### Post by Zerberus on 2011-05-01
For some reason I can edit the partition on my desktop now, but opening folders is really really slow....... never happened when my desktop was the partition in maverick, anyway here is the info you requested.

> 
sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008cb0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046    47859711    23928833    5  Extended
/dev/sda2   *    48837600   234436544    92799472+  83  Linux
/dev/sda3        47859712    48836607      488448   82  Linux swap / Solaris
/dev/sda5            2048    47859711    23928832   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00024509

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   234440703   117219328    b  W95 FAT32




> 
mount

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda2 on /home/zerberus/Desktop type ext4 (rw,commit=0)
gvfs-fuse-daemon on /home/zerberus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zerberus)
/dev/sdb1 on /media/3B3D-63B6 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)













> 
sudo blkid

/dev/sda3: UUID="c00ae2bd-f572-4447-baa7-a89a5eb296a7" TYPE="swap" 
/dev/sda2: LABEL="Personal" UUID="71f3ddb0-a22b-445f-b2b7-185861ebaf1e" TYPE="ext4" 
/dev/sda5: UUID="ae7741d5-2361-44ac-8ba8-1b6dad6025ad" TYPE="ext4" 
/dev/sdb1: UUID="3B3D-63B6" TYPE="vfat" 





> **coffeecat said:**
> There was a bug that manifested just before final release - hence no time to fix it - that prevented you from typing in a custom mount point in the manual/advanced option, or whatever it's called now. Bug here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

Fwiw and for future reference, the workaround is to boot into the live desktop rather than go straight to the installer. Open gedit, type in your mountpoint and copy it into the clipboard with ctrl-C. Don't close gedit. Now start the installer and when you get to where you want to specify a mountpoint, right-click on the field and paste what's in the clipboard. You have to right-click to choose paste from the context menu, not left-click and ctrl-V - that doesn't work.

Anyway...

First comment: I think mounting a partition to the desktop is not advisable. I've never tried it - I don't think I ever will. A custom folder in home might be better. Whatever, so long as your 96GB is on sda2 then your fstab looks OK. So let's investigate. Post the output of these terminal commands:

```
sudo fdisk -lu
sudo blkid
mount
```**Please** post the output between [noparse]```
 and 
```[/noparse] tags for clarity. You will lose essential formatting if you don't.

---

### Post by coffeecat on 2011-05-01
Since it's working now, there's not really much you can do. The mount command shows it is mounted OK. It might be worth changing this line in /etc/fstab:

```
/dev/sda2       /home/zerberus/Desktop  ext4  defaults       0  0
```To this:

```
UUID=71f3ddb0-a22b-445f-b2b7-185861ebaf1e       /home/zerberus/Desktop  ext4  defaults       0  0
```It's more dependable, but I doubt whether it will make anything faster. Just to repeat - mounting to your desktop is not a good idea. Have a think about powerpleb's idea of mounting to /mnt and setting up a symlink to somewhere in your home. The symlink could be a folder on your desktop rather than making the whole of the desktop the place you see the contents of sda2.

By the way, you used quote tags, not code tags. You need code tags for terminal output.

---

### Post by Zerberus on 2011-05-01
thanks for the reply, I will use it for my fourth install of natty! Gnome 3 + Natty doesn't seem to work!

---

