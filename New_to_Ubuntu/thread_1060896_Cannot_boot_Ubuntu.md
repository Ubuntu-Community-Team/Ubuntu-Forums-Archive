---
title: "Cannot boot Ubuntu"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by isdfe5 on 2009-02-05
Hi All

New to all of this so sorry if this is a stupid question. I have Ubuntu on a hard drive and it boots fine on one SATA port, but I need to move the disk to a different port, i.e. plug it into a different SATA port. I then try to boot from the drive and it fails with "ALERT: /dev/disk/by-uuid XXXXXX not found". This is the same drive that boots in the first SATA port. Note: I can see the data on the drive on this port if I boot into Windows (using the extfs add-on). For some reason I had assumed the uuid wouldn't change just because I'd changed SATA port...

After it has failed to boot and dropped into the emergency BusyBox shell I can do "ls -l /dev/disk/by-uuid" and I can see a uuid, but the format of it is nothing like the format of the uuid in the startup script that runs via the Grub loader. Is it correct that it is a different format and if so what do I need to change to get it to boot from this new SATA port (it will most likely stay on this port). However is there a way of setting things up so that the drive will boot from any port?

I'm becoming more and more itnerested in Ubuntu, but having to swap SATA leads over to boot is a little annoying... :(

Thx for any help
Chris

---

### Post by 73ckn797 on 2009-02-05
Are there any other hard drives in the system? If so then the system may be looking for a different designation. Might need to see your grub "menu.lst" boot info. If you are swapping 2 drives between two connections, that would confuse grub cause it may be looking for the unique uuid at a different location than where you moved it to.

---

### Post by isdfe5 on 2009-02-05
Hi

Thanks for replying. Unfortunately I'm still really new to all this. More than happy to provide the grub "menu.lst" boot info only I'm not sure what I need to do in order to get this to you. At the moment with the current config the boot fails and I get dropped into a BusyBox shell. Can I get the list from there? If not then I can set the PC so it will boot Ubuntu. However this is not the config I want to end up with finally, although this might not be a problem?

I have read that I should be using things like sda1 rather than uuid anyway - is that right?

Finally could you clarify what an uuid actually is!

Sorry for all the questions, but it will sink in :)

Thx
Chris

---

### Post by 73ckn797 on 2009-02-05
> **isdfe5 said:**
> Hi

Thanks for replying. Unfortunately I'm still really new to all this. More than happy to provide the grub "menu.lst" boot info only I'm not sure what I need to do in order to get this to you. At the moment with the current config the boot fails and I get dropped into a BusyBox shell. Can I get the list from there? If not then I can set the PC so it will boot Ubuntu. However this is not the config I want to end up with finally, although this might not be a problem?

I have read that I should be using things like sda1 rather than uuid anyway - is that right?

Finally could you clarify what an uuid actually is!

Sorry for all the questions, but it will sink in :)

Thx
Chris

Set up the computer to where it can boot up. Once you are in Ubuntu go to the top panel under Applications/Accessories/Terminal.

Once that opens enter the following commands, one at a time. Please copy the info and paste into your next message.

First, in order to access the grub "menu.lst" enter:

```
gksudo gedit /boot/grub/menu.lst
```Copy what will appear similar to the following at the end of the file:
```

## ## End Default Options ##

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 32bit 8.10, memtest86+
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Home Edition sp3
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```Next type in the following and paste into your reply:

```
sudo fdisk -l
```It will prompt for your password.

Copy the info that will appear similar to the following:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00009db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076969

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18701   150215751   83  Linux
/dev/sdb2           18702       19457     6072570    5  Extended
/dev/sdb5           18702       19457     6072538+  82  Linux swap / Solaris


```Enter "exit" to close the terminal or click the "X" at top right corner.

The **UUID** (Universally Unique Identifier) of the hard drive. Call it a serial number.

Designating whether the drive is sda1 and/or (hd0,0) or whatever can affect how the system starts up.

You also need to be aware of the other helpful info available. Such as:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

Those sources will answer many questions about Ubuntu and how to get around.

---

### Post by isdfe5 on 2009-02-06
Hello

Thank you for the instructions and I think here is the info you asked for.

First /boot/grub/menu.lst:
```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4983b885-2d45-4c08-a772-d6c81195838b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4983b885-2d45-4c08-a772-d6c81195838b ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4983b885-2d45-4c08-a772-d6c81195838b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4983b885-2d45-4c08-a772-d6c81195838b ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

There is nothing after that (Ubuntu is the only OS on this drive).

And now output from sudo fdisk -l:
```

user@user-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6f56c73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2310    18555043+  83  Linux
/dev/sda2            2433       38913   293033632+  83  Linux
/dev/sda3            2311        2432      979965   82  Linux swap / Solaris

Partition table entries are not in disk order
user@user-desktop:~$ 

```

This configuration boots okay. I did try altering the boot/grub/menu.lst and /etc/fstab files to use sda1 etc instead of UUIDs, but it didn't work. Ubuntu failed to boot, saying it could not find files on /sbin/init or something. I've changed it back now, although you can see what I changed it to in the menu.lst above (I commented out the changes and uncommented the original statements). I have also included the /etc/fstab file for completeness below (since I did make changes - backed out - to this):
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# /dev/sda1
UUID=4983b885-2d45-4c08-a772-d6c81195838b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1 /               ext3    relatime,errors=remount-ro 0       1
#
# /dev/sda2
UUID=94f4a9ef-3b3f-4f68-aafc-244c40a62ccf /home           ext3    relatime        0       2
# /dev/sda2 /home           ext3    relatime        0       2
#
# /dev/sda3
UUID=9c4794fb-c133-4484-b3dd-c00a05e5e7e5 none            swap    sw              0       0
# /dev/sda3 none            swap    sw              0       0
#
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Finally thanks again for the help - once I can get the disk booting on the other SATA port I'll be fine. The only "hardware" change I am making is to use a different SATA port for the drive (which is why I don't understand that if the UUID is the disk that it can make a difference which SATA port you use to connect it to the mobo?).

Cheers
Chris

---

