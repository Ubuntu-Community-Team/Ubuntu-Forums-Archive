---
title: "cdrom not detected in 9.10"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by cslav on 2009-11-09
Seems like this is a major bug.  I've researched it on Launchpad and performed an apport to  the site.  Been previously reported and based on the posts there it seems that Houston has a problem.  My 9.10 install also did not detect my cdrom.  Thinking it was a hardware problem I reset the pins to slave.  The system recognized it then (as cdrom0),  but would not mount (with ANY data in it).  Sees USB sticks immediately.  Anyway, after spending the better part of all day digging around, I re-installed 8.10 and no problems.  I'm a complete noob, but did do a thorough google search of the issue and made the best attempts I could with the suggested solutions I discovered, and concluded that, at this time, the issue is best left in more capable hands than myself.  I would guess that this "regression" will be taken care of in the new release.  In the meantime, I'm just as happy running 8.10.  I love this distro for starting out and am using it to learn LINUX! not just Ubuntu.

Best regards,
Charles

---

### Post by lavinog on 2009-11-10
Did it work in 9.04?

can you post the output of the following in 8.10
```

dmesg|grep 'ATAPI'

```
if nothing shows up post the output of dmesg.

---

### Post by mpentney on 2009-11-10
My new 9.10 installation is also now not seeing the CDROM. It worked OK during installation and for a day or two afterwards, but it now doesn't seem to do anything when I insert an audio CD.

Output of "dmesg | grep 'ATAPI'" is:

[    1.353258] ata5.00: ATAPI: HP  DVD Writer 400, Bh04, max UDMA/33

Any suggestions?

TIA,

Mike.

---

### Post by ukripper on 2009-11-10
> **mpentney said:**
> My new 9.10 installation is also now not seeing the CDROM. It worked OK during installation and for a day or two afterwards, but it now doesn't seem to do anything when I insert an audio CD.

Output of "dmesg | grep 'ATAPI'" is:

[    1.353258] ata5.00: ATAPI: HP  DVD Writer 400, Bh04, max UDMA/33

Any suggestions?

TIA,

Mike.

Can you run below commands and post output here:
```
ls -al /dev/cdrom0
```
and 
```
mount
```

```
cat /etc/fstab
```

---

### Post by mpentney on 2009-11-10
ukripper:

Thanks for the reply to my post. Here is the output of the commands you suggested.

```


mike@mike-desktop:~$ ls -al /dev/cdrom0
ls: cannot access /dev/cdrom0: No such file or directory


mike@mike-desktop:~$ ls -al /media/cdrom0
total 8
drwxr-xr-x 2 root root 4096 2009-11-05 11:33 .
drwxr-xr-x 5 root root 4096 2009-11-06 16:44 ..


mike@mike-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/backup type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//192.168.1.11/mike on /media/nas01-mike type cifs (rw,mand)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)



mike@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2e7906b5-8ea3-41be-938b-6567fb8337a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a543e546-2d98-455c-9fd1-77654350db1d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# mount old hard drive
/dev/sdb1       /media/backup  ext3 defaults 0 2
# mount NAS disk
//192.168.1.11/mike /media/nas01-mike cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
mike@mike-desktop:~$ 


```

So there's an entry in fstab for the CDROM but it doesn't appear to have been mounted....

TIA,

Mike.

---

### Post by ukripper on 2009-11-10
Can you manually try mounting your CDROM. try below command:
```
sudo mount /dev/scd0 /media/cdrom0
```

and can you also post output of this command:
```
ls -al /dev/cdrom
```

---

### Post by mpentney on 2009-11-10
Hi, ukripper.

Here are the results:

```

mike@mike-desktop:~$ sudo mount /dev/scd0 /media/cdrom0
[sudo] password for mike: 
mount: /dev/sr0: unknown device

```

and

```

mike@mike-desktop:~$ ls -al /dev/cdrom
lrwxrwxrwx 1 root root 3 2009-11-10 08:18 /dev/cdrom -> sr0

```

Thanks again for your help.

Mike.

---

### Post by ukripper on 2009-11-10
> **mpentney said:**
> Hi, ukripper.

Here are the results:

```

mike@mike-desktop:~$ sudo mount /dev/scd0 /media/cdrom0
[sudo] password for mike: 
mount: /dev/sr0: unknown device

```

and

```

mike@mike-desktop:~$ ls -al /dev/cdrom
lrwxrwxrwx 1 root root 3 2009-11-10 08:18 /dev/cdrom -> sr0

```

Thanks again for your help.

Mike.

Can you change cdrom group with this command and try again to mount it, first do this:
```
sudo chown root:cdrom /dev/sr0
```

and then just run below command:
```
sudo mount /dev/scd0 /media/cdrom0
```

and see if it mounts

---

### Post by mpentney on 2009-11-10
Hi, ukripper.

Same result:

```

mike@mike-desktop:~$ sudo chown root:cdrom /dev/sr0
[sudo] password for mike: 

```

```

mike@mike-desktop:~$ ls -al /dev/scd0
lrwxrwxrwx 1 root root 3 2009-11-10 08:18 /dev/scd0 -> sr0

```

```

mike@mike-desktop:~$ sudo mount /dev/scd0 /media/cdrom0
mount: /dev/sr0: unknown device

```

TIA,

Mike

---

### Post by ukripper on 2009-11-10
Can you reboot and select recovery from grub screen and then try to see if recovery detects the cdrom?

---

### Post by lavinog on 2009-11-10
see if dmesg reports your cdrom in 9.10.
```
dmesg|grep 'ATAPI'
```

---

### Post by ukripper on 2009-11-10
Can you put your cd you trying to mount in cdrom and then run below command:
```
blkid /dev/sr0
```

i thought this problem was fixed on launchpad in apha5.

Can you try to boot into ubuntu with the Cd in , i believe it should mount fine as some kernel bug was reported in early development of Karmic. [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/431055](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/431055)

---

### Post by mpentney on 2009-11-10
ukripper:

Rebooting seems to have fixed the problem for the moment, though I wasn't able to get into recovery mode! (After selecting recovery mode in the grub menu, I was offered a 2nd menu of choices but my USB keyboard and mouse were frozen and I could only reboot again....)

I'll post to this thread again if my CDROM stops working over the next few days and the various suggestions you've made don't help.

Thanks again,

Mike.

---

