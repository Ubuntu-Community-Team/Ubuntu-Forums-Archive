---
title: "Harddisk- NTFS, wits end!"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Andyc709292 on 2009-05-01
Hi all,
I've got a nice installation of 9.04 going, even got the dual monitor thing going, but I'm having a mare with a drive that's internal on my machine.

Essentially it's a seperate (on board) SATA controller on a NFS2 mainboard, 250Gb NTFS drive.

Whilst installing it was disabled in the BIOS, building my Ubuntu on the primary standard IDE controller.

So, now it's turned on, and I can manually mount it, read what's on there and do all that.

But I don't own the drive, so it seems that I can't do anything much with it.

I have a link to a text file and I want to uncheck that it's exectutable so my other half can just open it without a warning. And I'd like to have it mounted on startup.
Now, I've read heaps, (and embarrassingly) talked with my team about it at work, being in IT as I am... complete with Ubuntu users there...

So, I've tried editing Fstab, I've tried the NTFS-config (0.5.5.), I've read hours of postings on this and really is it a case of the drive is NTFS and not mine any more...???!!!

Mount info:
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/home/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=home)
/dev/sda1 on /media/Images type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

ls -l /media:
total 12
lrwxrwxrwx 1 root root    6 2009-04-27 21:28 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-04-27 21:28 cdrom0
drwxr-xr-x 2 root root 4096 2009-04-27 21:28 cdrom1
drwxrwxrwx 1 root root 4096 2009-05-01 20:26 Images

I've sudo'd to the point that I've looked up the dictionary meaning of the word in case I've missed something.... Now I can type sudo -i without actually thinking it.

Sanity in form of step by step guide needed (I'll only ask once!) - oh, formatting last resort as has 200Gb of family images etc on there (backed up but who wants to test that so readily, esp as it's a Windows/Nero backup...).

help.

---

### Post by skymera on 2009-05-01
Hmm i've always had read/write permissions on the drives i mount.

How did you mount the drives?
Did you..

```
 udo su
mount /dev/<device>

```

or just use

```
 sudo mount /dev/blah 
``` 

This is my output, i have full read/write

```
scott@scott-desktop:~$ ls -l /media
total 24
lrwxrwxrwx 1 root root     6 2009-04-24 15:58 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2009-04-24 15:58 cdrom0
drwxr-xr-x 2 root root  4096 2009-04-24 15:58 cdrom1
drwxrwxrwx 1 root root 16384 2009-04-27 22:25 windows

```

---

### Post by Andyc709292 on 2009-05-01
home@main:~$ udo su
Error:  0: couldn't open source file <su.ui>
su.ui: No such file or directory

(That after installing it just now).

No luck with that - personally I've just clicked on the drive icon in the places menu and away I've gone... 
Fstab probably would work if I could edit it... but that's no doubt another thing I don't have rights to.

Funny, root over here in Aus has another meaning altogether, I'm starting to see why! ;o)

---

### Post by Andyc709292 on 2009-05-01
Actually looking at it, you've got the same rights as me on your windows drive. So can you change permissions on files in there, or change a text file to be non executable?

---

### Post by SuperSonic4 on 2009-05-01
I suspect that first command is ```
sudo su
```

You might be able to chmod or chown them I suppose, check the man pages for more info

---

