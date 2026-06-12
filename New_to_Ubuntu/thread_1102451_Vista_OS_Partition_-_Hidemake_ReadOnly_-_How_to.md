---
title: "Vista OS Partition - Hide/make ReadOnly - How to?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by deadmanschest on 2009-03-21
Hi all - laptop with 64bit U8.10 and Vista dual booting.

Single HDD with mulitple partitions in NTFS and U8.10 on ext2 or 3.

Problem - the file manager in U8.10 shows all partitions, including my VistaOS and Data partition, as well as other media partitions that I do want to 'share' between Ubuntu and Windows, as "Removable Media", same as any USB flash drive.

When I simply mouse over any of these 'drives' they are "mounted" immediately.

I want to make it harder to mount the VistaOS and VistaData partitions to protect them. I don't mind having access, but not by accident. If there is a crash or hard shutdown I don't want to have damage between Os's...s 

I would be happy to make it harder to mount any of the HDD partitions, because the mouse-over effect is irritating when just looking for a file in U8.10 and suddenly having a desktop full of drives.....

Ideas?

Thanks

---

### Post by davmac on 2009-03-22
If you open up a terminal and enter "sudo gedit /etc/fstab" you'll see the list of drives that are automatically mounted at start up. Do you see your Vista partition here? If so you can just comment out the line by putting a # at the start.

You can also mount it as read only. Have a read of [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) for more info about the fstab file.

Hope this helps,

Dave Mac

---

### Post by deadmanschest on 2009-03-22
> **davmac said:**
> If you open up a terminal and enter "sudo gedit /etc/fstab" you'll see the list of drives that are automatically mounted at start up. Do you see your Vista partition here? If so you can just comment out the line by putting a # at the start.

You can also mount it as read only. Have a read of [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) for more info about the fstab file.

Hope this helps,

Dave Mac

Hi Dave - thanks for the note - I ran the terminal command and am told that the command is not recognized...

Small clarification - I don't believe that any of the partitions are "mounted automatically" but as close to automatic as one can get...hehe..as I say simply by mouse-over.

I have scanned the link you gave, but I cannot find the fstab file in etc/
Assuming I have no /fstab file, is there any other mod I can do to make it harder to mount the Windows partitions?

Thanks - enjoy Spring!

dmc

PS - screenshot of the file manager window below - shows the etc/ file with no fstab, and also all the partitions on the left pane, if I mouse over any of them, they mount immediately....

Cheers

---

### Post by davmac on 2009-03-22
Hmmm.

If you mount the Vista partition and then open up a terminal and type in "mount" can you copy/paste in what you get?

Thanks.

---

### Post by deadmanschest on 2009-03-23
> **davmac said:**
> Hmmm.

If you mount the Vista partition and then open up a terminal and type in "mount" can you copy/paste in what you get?

Thanks.

Hi Dave - got called away..A day later here is the cut/paste

control@lilblue:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/control/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=control)
/dev/sda1 on /media/VISTAOS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
control@lilblue:~$ 

dev/sda 2 is the linux partition, no swap as 4GB Ram, dev/sda 1 at the end is the Vista OS partition.

Thanks

dmc

---

### Post by BGFG on 2009-03-23
Try the code davemac gave you again, without the quotes
```

sudo gedit /etc/fstab

```

once inside, edit the unwanted lines using the # sign.
My fstab looks like this:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=969dcd38-350e-48e4-8c40-3fd77c7bb789 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdc5 during installation
UUID=1d74452c-f88b-4550-a736-f179e0fa3742 /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Note the '#' signs,used to add text to the file, but not affecting anything. If i wanted to remove the cdrom, I'd do this:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=969dcd38-350e-48e4-8c40-3fd77c7bb789 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdc5 during installation
UUID=1d74452c-f88b-4550-a736-f179e0fa3742 /home           ext3    relatime        0       2
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

try the same for your vista drive.

---

### Post by deadmanschest on 2009-03-24
> **BGFG said:**
> Try the code davemac gave you again, without the quotes
```

sudo gedit /etc/fstab

```

once inside, edit the unwanted lines using the # sign.......



[balance snipped by dmc]

Hi BGFG - thanks for the note. I ran the fstab command again, and now it works (following using 'mount') BUT only my linux partition and DVD drive show up.....that includes when having the VistaOS and Data partitions mounted already....?

Here's the output (remember with 2 'removable drives' mounted - that is how U8.10 shows my other partitions, as removable drives)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c7c3bc38-4743-4d97-821a-d32128423aee /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Any other ideas?

Thanks

dmc

---

