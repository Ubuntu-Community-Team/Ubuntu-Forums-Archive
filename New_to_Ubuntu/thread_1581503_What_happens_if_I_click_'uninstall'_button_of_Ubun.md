---
title: "What happens if I click 'uninstall' button of Ubuntu in Windows 7?"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by mr.xulu on 2010-09-25
Hi! My netbook, Lenovo S10-3 ideapad, is on dual boot with lucid (plus lubuntu meta package) and windows 7 starter ed.

I noticed that when I'm in Windows 7 and I go to 'start menu' and then 'computer' then click on 'uninstall or change a program' that Ubuntu 10.04.1 is listed there.

If I click on that and try to uninstall Ubuntu using that method, will everything be restored back to the way it was before I installed Ubuntu including reconfiguring the partitions back to their original configuration?

I haven't been one month yet on Ubuntu and enjoying it very much. But I never looked into how to uninstall it in case something goes wrong with Ubuntu like a crash or something.

This knowledge will come in handy in case I have a need to uninstall Ubuntu for some reason in the future.

Hope someone can help. Thanks a lot! :)

---

### Post by beew on 2010-09-25
Well you are running WUBI, that is not a real dual boot.*Wubi is a Windows program.* It just creates a  virtual play pen that exists in a Windows folder. If you click uninstall WUBI would be gone like other Windows programs would (and remove the folder where 'Ubuntu' lives). If you  want to experience Ubuntu for real you should install it in a separate partition to give it equal status to Windows.

---

### Post by mr.xulu on 2010-09-25
> **beew said:**
> Well you are running WUBI, that is not a real dual boot.*Wubi is a Windows program.* It just creates a  virtual play pen that exists in a Windows folder. If you click uninstall WUBI would be gone like other Windows programs would (and remove the folder where 'Ubuntu' lives). If you  want to experience Ubuntu for real you should install it in a separate partition to give it equal status to Windows.


Hi beew! I installed lucid using this link:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I downloaded lucid (section 1) and installed it first on live usb and tried it out(section 2 and 3). then I liked it so from live usb I clicked the "install ubuntu 10.04" icon that was displayed on the desktop and followed the instructions in section 4.

At one point in the install process is "Prepare disk space" and I chose "install them side by side, choosing between them each start up". I was even able to create a partition for it and gave it 30.2 gb using that graphical slide bar and it even automatically made a swap partion of about 1.8gb.

Every time I turn my computer on or restart i get the GNU GRUB menu to choose which OS I want.  

Is this a Wubi install or dual boot?

By the way I don't see "Wubi" listed on the windows 7 menu for "uninstall or change a program". What is listed is "Ubuntu 10.04.1".

Hope you can clarify for me what kind of install I made so I can get the proper instructions for uninstall should it be needed.

Thanks a lot! :)

---

### Post by Elfy on 2010-09-25
Inside your ubuntu installation - open a terminal from the apps -accessories menu and run this command

```
sudo fdisk -l
```

```
mount
``` will tell you what is mounted and where

If you have a 'real' installation you should see at least one linux partition, if you don't it is probably wubi. If you are not sure post it here - inside CODE tags please. 

That is [noparse]```
[/noparse] at the beginning of the paste and [noparse]
```[/noparse] at the end of the paste.

---

### Post by mr.xulu on 2010-09-25
> **forestpiskie said:**
> Inside your ubuntu installation - open a terminal from the apps -accessories menu and run this command

```
sudo fdisk -l
```

```
mount
``` will tell you what is mounted and where

If you have a 'real' installation you should see at least one linux partition, if you don't it is probably wubi. If you are not sure post it here - inside CODE tags please. 

That is [noparse]```
[/noparse] at the beginning of the paste and [noparse]
```[/noparse] at the end of the paste.


Hi forestpiskie! 

the command 'sudo fdisk -l' gave me this:

[code]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfbd6cb99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       20895   167625875+   7  HPFS/NTFS
/dev/sda3           20895       28476    60894209    f  W95 Ext'd (LBA)
/dev/sda4           28476       30402    15471800   12  Compaq diagnostics
/dev/sda5           24524       28476    31737856    7  HPFS/NTFS
/dev/sda6           20895       24369    27907072   83  Linux
/dev/sda7           24369       24523     1240064   82  Linux swap / Solaris

Partition table entries are not in disk order [code]


the command 'mount' gave me this:

[code]/dev/sda6 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/m/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=m)[code]


Hope I did it right :)

Thanks a lot! :)

---

### Post by Elfy on 2010-09-25
It's not wubi - you ahve ubuntu installed on sda6. You have swap on sda7. Unless wubi has changed the way it installs, but I'm sure that it uses a virtual root disk.

You might have had a wubi install or maybe an aborted install - have a look here for some more info on that - [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

---

### Post by mr.xulu on 2010-09-25
Thanks a lot forestpiskie! :)

---

