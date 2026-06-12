---
title: "missing mount points for cd/dvd and cdrw"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-07-05
In the process of removing and reinstalling samba last night, I apparently checked off something in synaptic that was way wrong. When I hit 'apply' all of a sudden a long list of files went poof, with them the mount points for my cdrom and dvd burner. Now, neither drive works at all (unable to mount location) and when I try to boot from cd, I get a kernel panic. I changed the hard drive and it booted fine from cd, so it does not seem to be a physical problem with the computer. (I'm sure this is entirely self-inflicted). I'd just go ahead and reinstall Lucid LTS on the drive but I can't figure out how to do that considering the drive won't boot from cd.

Looking in places, I see cd/dvd drive, floppy and file system - cdrw is not showing

fstab shows - 

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0e22486f-d3a6-4396-bd74-e614aa2e8ecc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63bbd1e1-2045-414f-a918-9f5a5da7bc82 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```I searched through a lot of posts that described similiar problems and found on the forum suggested using  mkdir  to create a new directory for the cdrom, which I tried but nothing seems to happen. I attempted it again. Using the following commands I made one directory but when I attempted to do another for the second drive it said it already existed. 
[http://ubuntuforums.org/showthread.php?t=1100772](http://ubuntuforums.org/showthread.php?t=1100772) has the following instructions so I tried using the code from it 

```
cd /media
sudo mkdir cdrom
sudo chown root cdrom
sudo chgrp root cdrom
sudo chmod 755 cdrom
sudo ln -s cdrom cdrom0
```It seemed to work the first time but it did not work for the second drive, saying it already existed.

How can I replace the missing mount points, please?

EDITED TO ADD - I just rebooted and now at least the cdrw is showing under Places/Computer. Hopefully that's a step in the right direction

ANOTHER EDIT - wodim was not detecting the devices so I installed cdrskin  now - 

```
 wodim --devices
0  dev='/dev/scd0'    rwrw-- : 'HL-DT-ST' 'DVD-RAM GH22NP21'
 1  dev='/dev/scd1'    rwrw-- : 'SONY' 'CD-RW  CRX175E'
```I'm very sketchy on how to proceed from here though.

thanks,

mystmaiden

---

