---
title: "Force mounting a hard disk"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by el_grimley on 2009-02-02
Hello

I've been moving slowly over to ubuntu over the last few months. Having finally got my copy of Photoshop running under wine I was preparing to move all my .psd etc over to my "files" drive from my Windows "C drive" and ditch the "C drive" as it was developing HD errors. Unfortunately the "C Drive" died mid boot (one of the famous mup.sys problems), I'm fairly certain I can get the files off it by booting it as the slave. (Note all are physical HDs and not partitions)

However I am more concerned with the "files" drive, which isn't mounting under ubuntu for me. I've tried force mounting it and following the instructions from these two threads 
[http://ubuntuforums.org/showthread.php?t=694301](http://ubuntuforums.org/showthread.php?t=694301)
[http://ubuntuforums.org/showthread.php?t=282913](http://ubuntuforums.org/showthread.php?t=282913)

This only leads to the following error "Failed to access volume '/dev/DRV2_VOL1': No such file or directory" which I am having no luck in resolving. Below is the output from terminal so you can see whats been going on.


Thanks

Graham

```

grimley@gphiv:~$ sudo mount /dev/DRV2_VOL1 /media/DRV2_VOL1 -o force
[sudo] password for grimley: 
mount: mount point /media/DRV2_VOL1 does not exist
grimley@gphiv:~$ sudo mkdir /media/DRV2_VOL1
grimley@gphiv:~$ sudo mount /dev/DRV2_VOL1 /media/DRV2_VOL1 -o force
mount: special device /dev/DRV2_VOL1 does not exist
grimley@gphiv:~$ lsusb
Bus 005 Device 002: ID 07ab:fcbf Freecom Technologies 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 15ca:00c3  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
grimley@gphiv:~$ sudo mount -t ntfs /dev/DRV2_VOL1 /media/DRV2_VOL1 -o -force
[sudo] password for grimley: 
ntfs-3g: Failed to access volume '/dev/DRV2_VOL1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
grimley@gphiv:~$ /sbin/mount.ntfs --help

ntfs-3g 1.2216 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=,
          syncio.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  http://ntfs-3g.org
grimley@gphiv:~$ sudo mount -t ntfs-3g /dev/DRV2_VOL1 /media/DRV2_VOL1 -o -force
ntfs-3g: Failed to access volume '/dev/DRV2_VOL1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

```

---

### Post by el_grimley on 2009-02-02
Problem fixed. Thanks to guys in Ubuntu-uk chat room Riceeey and brobostigon.

I wasnt using the name of the HD. This was found using "sudo fdisk -l".

Thanks

Graham

---

