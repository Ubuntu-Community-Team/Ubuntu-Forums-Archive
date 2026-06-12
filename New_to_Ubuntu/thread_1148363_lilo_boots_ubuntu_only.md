---
title: "lilo boots ubuntu only"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Franz01 on 2009-05-04
First ever installation of ubuntu... with some problems...

I tried the usual 8.10 iso but I got an error "executing grub-install (hd0) failed". The installation did not finish and I could not boot. Not sure why it did not work.

So I tried the "alternate" version. I received the usual "grub error" but the system prompted me with another choice: LILO. So I tried LILO and installation finished properly.

**The problem now is that I can boot Linux only**. What shall I do in order to have the choice WinXP or Linux?? I gave all the default options to LILO install...

Reading other posts I had a look at /etc/lilo.conf

boot=/dev/sda
map=/boot/map
delay=20
default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1
	append="root=/dev/sda2  "
	initrd=/initrd.img

other=/dev/sda1
	label=Windows

Not sure what I have to do....please let me know...

I have first partition with XP, I formatted partition #2 as ext3.
The full info for the partitions is here:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5957    47849571    7  HPFS/NTFS
/dev/sda2            5958        7257    10442250    7  HPFS/NTFS
/dev/sda3            7258        7296      313267+  82  Linux swap / Solaris

Thank you very much for your suggestions!

---

### Post by apienk01 on 2009-05-04
Did you start the install from within Windows using wubi executable, or did you boot from the Ubuntu LiveCD?

---

### Post by Franz01 on 2009-05-04
> **apienk01 said:**
> Did you start the install from within Windows using wubi executable, or did you boot from the Ubuntu LiveCD? 
I used ubuntu alternate liveCD

---

### Post by apienk01 on 2009-05-04
But did you BOOT from the LiveCD - I mean putting it into your CDROM before the computer starts? Or you started up Windows, and then put the CD in and chose install? This is important because your Windows software could block GRUB writing the Master Boot Record of your hard disk.

Anyway, your /etc/lilo.conf looks correct. You should be able to boot Windows by pressing Tab during boot. Just after your computer powers up you should see a message (more or less): "press Tab to see a list of operating systems". If you want to be automatically asked which system to start at every boot, edit /etc/lilo.conf and add a line saying "prompt". Then run "sudo lilo -v" in a terminal to update the Master Boot Record. Your lilo.conf should look like this:

boot=/dev/sda
map=/boot/map
delay=20
prompt
default=Linux

image=/vmlinuz
label=Linux
read-only
# restricted
# alias=1
append="root=/dev/sda2 "
initrd=/initrd.img

other=/dev/sda1
label=Windows

EDIT: Is your linux partition formatted as NTFS? I would advise to reinstall ubuntu and reformat to ext3 or ext4. It is a much better and linux-native filesystem.

---

### Post by Franz01 on 2009-05-04
> **apienk01 said:**
> But did you BOOT from the LiveCD - I mean putting it into your CDROM before the computer starts? Or you started up Windows, and then put the CD in and chose install? This is important because your Windows software could block GRUB writing the Master Boot Record of your hard disk
I inserted the live CD and then I rebooted. I understand your point that Windows could block GRUB writing if I boot Win first... but for some reasons it happened.


> **apienk01 said:**
> 
Anyway, your /etc/lilo.conf looks correct. You should be able to boot Windows by pressing Tab during boot. Just after your computer powers up you should see a message (more or less): "press Tab to see a list of operating systems". If you want to be automatically asked which system to start at every boot, edit /etc/lilo.conf and add a line saying "prompt". Then run "sudo lilo -v" in a terminal to update the Master Boot Record. 


**Now it works! I did not run the "sudo lilo -v"  command** Thank you for your suggestion.

> **apienk01 said:**
> 
EDIT: Is your linux partition formatted as NTFS? I would advise to reinstall ubuntu and reformat to ext3 or ext4. It is a much better and linux-native filesystem.

I formatted the linux partition as ext3 (during the manual install). For some reasons when I run the "sudo fdisk -l" I cannot see ext3, but I see something different instead. Unless I do not understand something... if I have other options (i.e. commands for file system checking) plse let me know...

---

### Post by apienk01 on 2009-05-04
> I formatted the linux partition as ext3 (during the manual install). For some reasons when I run the "sudo fdisk -l" I cannot see ext3, but I see something different instead. Unless I do not understand something... if I have other options (i.e. commands for file system checking) plse let me know...

You must have forgot to tick "format" after choosing the etx3 filesystem. Now the only way to change it is reinstalling. Ubuntu should work on NTFS, but the ability to write NTFS filesystems is quite new in linux so numerous bugs may still be present. I would suspect problems with file ownership and linking.

---

### Post by Franz01 on 2009-05-04
> **apienk01 said:**
> You must have forgot to tick "format" after choosing the etx3 filesystem. Now the only way to change it is reinstalling. Ubuntu should work on NTFS, but the ability to write NTFS filesystems is quite new in linux so numerous bugs may still be present. I would suspect problems with file ownership and linking.

I am running Win XP now and what I do not understand is why I see NTFS in C:\ and nothing in the two other partitions (where I loaded Linux and swap). See attachment. 
Is it not possible an error in the "sudo fdisk -l" command? Or do I miss something?
Thank you for your time. 
I'll switch to linux now in order to check more carefully...

---

### Post by apienk01 on 2009-05-04
You are seeing this because swap and ext3 filesystems are not natively supported by Windows. Swap is a special partition having the same role as the Windows swapfile. When the system needs more memory, it frees some of it by saving a chunk temporarily to harddisk. You will never see the contents of swap, either in Windows or in Linux. You can however make Windows see the contents of your ext3 partition (if that is really ext3) by using a small utility called [explore2fs]("http://www.chrysocome.net/explore2fs"). The access is read-only.

If your linux partition was NTFS then Windows should see it normally. I'm puzzled. Could you post the output of these two commands?

```
cat /etc/fstab
mount
```

---

### Post by Franz01 on 2009-05-05
**cat /etc/fstab**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7607e6aa-87f4-43e2-95f8-501d3deb7fb4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=d07cdc50-ab74-4b4d-ad1d-d9dfd92deaec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

**mount**
```

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/francesco/.Private on /home/francesco/Private type ecryptfs (ecryptfs_sig=cbd6dc63028e5602,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/francesco/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=francesco)

```

---

### Post by apienk01 on 2009-05-06
Everything is fine. You've got a NTFS partition for Windows, and one ext3 and one swap for Linux. If you would like to access files on your Windows partition you should be able to do it just by choosing it from the Places menu. It will automount.

---

