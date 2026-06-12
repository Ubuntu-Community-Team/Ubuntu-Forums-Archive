---
title: "Resizing a partition in dual boot config with multiple Ubuntu installs"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by asookazian on 2010-10-25
*[COLOR=Teal]Synopsis: I have 1GB of free space remaining on the extended sub-partition for my 10.10 installation.  I would like to resize the partition and also remove unused sub-partitions for 10.04 installations (w/o harming grub!)[/COLOR]*

I have a dual-boot config of Win7 and multiple Ubuntu partitions.  It's a long story but basically I had problems with grub and now I have Ubuntu installed in multiple partitions (two 10.04 and on 10.10).  Original install using wubi.

I currently only use Win7 and Ubuntu 10.10.  I have about 1GB left in the /sda/dev9 which is the 10.10 partition.  There is a 104GB extended partition.  Inside that partition, there are the following sub-partitions according to disk utility:

/dev/sda5: 46GB ext4
/dev/sda6: 2GB swap
/dev/sda7: 27GB ext4
/dev/sda8: 2.3GB swap

free space in /dev/sda: 23GB (outside of extended partition)

I would like to delete and/or reallocate all four sub-partitions above.  These are for 10.04 installations which I don't need.  I tried to delete them using gparted and parted but for various reasons it does not work.  From gparted, when I try to delete /dev/sda5, for example, I get: "unable to delete /dev/sda5: please unmount any logical partitions with a number higher than 5".  The only mounted partition seems to be /dev/sda9 (10.10).  When I try to unmount that one I get: "could not unmount.  most likely other partitions are also mounted on these mount points."  This may be b/c I am trying to unmount a partition which is currently active (i.e. I'm running this operation from 10.10 which is /dev/sda9).  I also tried the 'umount' command as follows:

```
asookazian@asookazian-desktop:~$ sudo umount -v /dev/sda9
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```Following is the parted output for 'print all':

```
(parted) print all                                                        
Model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16           diag
 2      41.9MB  10.8GB  10.7GB  primary   ntfs            boot
 3      10.8GB  193GB   182GB   primary   ntfs            boot
 4      216GB   320GB   104GB   extended
 5      216GB   262GB   46.4GB  logical   ext4
 6      262GB   264GB   2032MB  logical   linux-swap(v1)
 7      264GB   291GB   26.9GB  logical   ext4
 9      291GB   317GB   25.3GB  logical   ext4
10      317GB   318GB   1138MB  logical   linux-swap(v1)
 8      318GB   320GB   2319MB  logical   linux-swap(v1)
```Out of curiosity, how does wubi know how much space to allocate to a new partition when you do a dual-boot config installation (assuming Win7 is installed first)?

---

### Post by drs305 on 2010-10-25
You cannot unmount a paritition on which Ubuntu (or other OS) is running. Additionally, swap partitions in use must also be unmounted. An easy way to check if a partition is mounted in GParted is to look for the 'key' icon next to the partition listing in the lower pane.

Normally these types of partitioning operations are conducted from the LiveCD, so you can unmount all of them. Even when booting from the LiveCD you must unmount the swap partition (select it, then Partition, swapoff).

If you are deleting partitions, when you are done make sure you remount the partition on which your Ubuntu is located and reinstall grub to ensure it knows where to find the Grub files. Do this before you reboot. Substitute the correct values for X and Y:```

sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdX
```
Note you designate the partition in the first command but only the drive in the second.

Also note you only need one swap partition, regardless of how many linux OS installs you have. Just make sure they point to the same one.

---

### Post by asookazian on 2010-10-25
Thanks for the informative reply.  I followed your instructions and deleted several partitions via the 10.10 LiveCD and GParted.  The problem now is the following:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
```

Here is the subsequent parted output:

```
(parted) print all                                                        
Error: /dev/sr0: unrecognised disk label 
```

Now /dev/sda4 is extended.
/dev/sda5 is ext4 (the 10.10 partition that is running out of space).
/dev/sda6 is swap.

There is over 90GB unallocated space available now.

Must I mount /dev/sda4 as well?  If so, what are all the commands I need to exec now?

Please advise.

---

### Post by asookazian on 2010-10-25
I just tried to increase (resize) /dev/sda5 and it failed immediately.  No error displayed.  However, when GParted refreshed the GUI, now /dev/sda4 and /dev/sda5 have keys next to them and the mount point for /dev/sda5 is /mnt.

---

### Post by asookazian on 2010-10-25
```
ubuntu@ubuntu:/etc/grub.d$ sudo grub-install -v /dev/sda
grub-install (GRUB) 1.98+20100804-5ubuntu3

```

Is this the correct version of GRUB to be using?

---

### Post by asookazian on 2010-10-25
```
ubuntu@ubuntu:/etc/grub.d$ sudo grub-probe -v /dev/sda
grub-probe: info: cannot open `/boot/grub/device.map'.
grub-probe: info: changing current directory to /dev.
grub-probe: info: changing current directory to snd.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to cpu.
grub-probe: info: changing current directory to shm.
grub-probe: info: changing current directory to disk.
grub-probe: info: changing current directory to by-uuid.
grub-probe: info: changing current directory to by-label.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to by-id.
grub-probe: info: changing current directory to dri.
grub-probe: info: changing current directory to bsg.
grub-probe: info: changing current directory to char.
grub-probe: info: changing current directory to block.
grub-probe: info: changing current directory to pts.
grub-probe: info: changing current directory to mapper.
grub-probe: info: changing current directory to input.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to by-id.
grub-probe: info: changing current directory to bus.
grub-probe: info: changing current directory to usb.
grub-probe: info: changing current directory to 002.
grub-probe: info: changing current directory to 001.
grub-probe: info: changing current directory to net.
grub-probe: info: changing current directory to pktcdvd.
grub-probe: error: cannot find a device for /dev/sda (is /dev mounted?).
ubuntu@ubuntu:/etc/grub.d$ sudo grub-probe -v /dev/sda5
grub-probe: info: cannot open `/boot/grub/device.map'.
grub-probe: info: changing current directory to /dev.
grub-probe: info: changing current directory to snd.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to cpu.
grub-probe: info: changing current directory to shm.
grub-probe: info: changing current directory to disk.
grub-probe: info: changing current directory to by-uuid.
grub-probe: info: changing current directory to by-label.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to by-id.
grub-probe: info: changing current directory to dri.
grub-probe: info: changing current directory to bsg.
grub-probe: info: changing current directory to char.
grub-probe: info: changing current directory to block.
grub-probe: info: changing current directory to pts.
grub-probe: info: changing current directory to mapper.
grub-probe: info: changing current directory to input.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to by-id.
grub-probe: info: changing current directory to bus.
grub-probe: info: changing current directory to usb.
grub-probe: info: changing current directory to 002.
grub-probe: info: changing current directory to 001.
grub-probe: info: changing current directory to net.
grub-probe: info: changing current directory to pktcdvd.
grub-probe: error: cannot find a device for /dev/sda5 (is /dev mounted?).


```

---

### Post by asookazian on 2010-10-25
contents of /etc/fstab:

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda10 swap swap defaults 0 0
/dev/sda6 swap swap defaults 0 0
/dev/sda8 swap swap defaults 0 0

```

---

### Post by asookazian on 2010-10-25
```
ubuntu@ubuntu:/dev$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /mnt type ext4 (rw)

```

---

### Post by asookazian on 2010-10-25
```
ubuntu@ubuntu:/mnt/arbitest$ sudo mount --bind /dev /mnt/arbitest/new
ubuntu@ubuntu:/mnt/arbitest$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu@ubuntu:/mnt/arbitest$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /mnt type ext4 (rw)
/dev on /mnt/arbitest/new type none (rw,bind)


```

---

### Post by asookazian on 2010-10-25
I tried SGD 0.9799 and that did not help at all no matter what I tried from the menus.  Apparently it cannot repair GRUB/MBR.  I think I'm more screwed than last time I had issues with MBR/GRUB.  The way I "fixed" it last time was by re-installing 10.04 again.  Thus, all the 10.04 partitions.

I will try restarting the box to see what happens w/o the LiveCD...

---

### Post by asookazian on 2010-10-25
Restart w/o LiveCD resulting in "No such partition" and then system displays the "grub rescue>" prompt.

Please advise.

---

### Post by drs305 on 2010-10-25
Run it this way:

```
sudo mount /dev/sd**XY** /mnt
sudo grub-install --root-directory=/mnt/ /dev/sd**X**
```

Note no number in the second command.

---

### Post by asookazian on 2010-10-25
You were a little too late but thanks for responding again.

I reinstalled 10.10 via the LiveCD and that seems to have fixed it (at least I have a 10.10 with almost 100GB partition that works).  Need to test Win7 to see if that is working.

But I ended up mounting the new 99GB partition to / (root).  Not sure if that matters or not.

---

