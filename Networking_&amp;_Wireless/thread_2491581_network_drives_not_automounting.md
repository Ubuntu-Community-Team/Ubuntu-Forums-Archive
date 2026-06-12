---
title: "network drives not automounting"
date: 2023-10-13
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2023-10-13
I have two external hard drives connected to a miniPC (also running 20.04) that it is serving to the network using samba. These drives are accessed by a wide range of devices - windows, linux, android, media players... 

I recently upgraded my shop system (one of the computers on the network) from 16.04 to 20.04. Under 16.04, sometimes these network drives would automount at boot up, sometimes they wouldn't and I would have to run 'sudo mount -a' to get them to mount. Since I have upgraded to 20.04, these drives NEVER automount. I have tried adding '@reboot /bin/mount -a'  as a crontab entry, but that isn't mounting them, either. 

I know that one of the drives spins down if not accessed and has to spin back up, which takes several seconds. I don't know if that has anything to do with the issue or not, but figured I'd throw that out there, just in case. 

Could someone give me some advice on getting these to mount up reliably when the the system is started? 

This is what I currently have in fstab

```

# UUID=fa9d3519-6125-4121-9810-b2822e398780	/mnt/shop.data	 ext3  defaults 0	0
# UUID=df479888-2010-485f-a620-0fab6516fab6	/mnt/multimedia  ext4  auto,nofail,users,rw,exec,sync	0	0

```

---

### Post by TheFu on 2023-10-14
Those lines are comments.  Have you tried removing the comment character?

I also assume this isn't the full /etc/fstab file, since there's usually a header to provide hints what each of the 6 fields are for and mounts for booting areas and a few other items.

For any USB-connected device, which might not have a solid connection (which applies to all USB storage), I use **autofs**, so storage is mounted on-demand.  Autofs is a little more complex.  For now, just try removing the comment character (#) from those lines.  

BTW, for ext3/4 storage, the options I'd use are
```
defaults,nodev,nosuid    0     1
```
It is a really bad idea to prevent periodic fsck checks, which is what your options do.

---

### Post by rebeltaz on 2023-10-14
Crap. I'm sorry. I copied the wrong two entries. Here is the whole thing:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d11e0c72-1c30-4382-b728-707087699705 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=DEC6-C35E  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=aface0b1-b7b8-4850-8433-f21b71e64831 none            swap    sw              0       0


#/dev/sdb1 normally unless another SATA drive installed
# UUID=fa9d3519-6125-4121-9810-b2822e398780	/mnt/shop.data	ext3	defaults0	0
# UUID=df479888-2010-485f-a620-0fab6516fab6	/mnt/multimedia		ext4	auto,nofail,users,rw,exec,sync	0	0

//192.168.1.15/multimedia	/mnt/multimedia	cifs	defaults,nofail,username=derek,password=password,gid=derek,uid=derek	0	0

//192.168.1.15/shop.data       /mnt/shop.data cifs    defaults,nofail,username=derek,password=password,gid=derek,uid=derek  0       0

```

---

### Post by Morbius1 on 2023-10-14
Add another option to your list: **[COLOR="#FF0000"]x-systemd.automount[/COLOR]**

Like this:
> //192.168.1.15/multimedia	/mnt/multimedia	cifs	defaults,nofail,username=derek,password=password,gid=derek,uid=derek**[COLOR="#FF0000"],x-systemd.automount[/COLOR]** 0	0

Better?

---

### Post by rebeltaz on 2023-10-14
> **Morbius1 said:**
> Add another option to your list: **[COLOR="#FF0000"]x-systemd.automount[/COLOR]**

Like this:


Better?

That did seem to take care of it. Thank you so much!

---

