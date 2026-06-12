---
title: "CIFS share mounted, but no files fora long time?"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by mlarsendk on 2007-02-25
Hi All,

I'm trying to get some samba shares on my Synology DS106e NAS storage server mounted at boot time on my Ubuntu 6.10 powered laptop.

Connection is OK, I can browse to the files via smb://192.168.1.xx/sharename.
If I do that, I see the files immediately!

However, if I do (as root):
mount -t cifs //192.168.1.xx/sharename /media/mountpoint -o user=myname,passwd=mypass

It mounts fine, but if I go to the direcrtory there are no files in it.
mount command gives me (only relevant line):
//192.168.1.xx/sharename on /media/mountpoint type cifs (rw,mand)

no errors or anything in dmesg or messages

If I wait about 5 minutes, THE FILES APPEAR!

If I mount as smbfs, it works right away, but I can't get smbfs to mount properly from fstab (I'd have to specify "noauto" or the computer hangs on hald (in another thread this is listed as a bug).

Also, I'd like to use CIFS as opposed to smbfs as smbfs is probably not going to be maintained anymore as CIFS is supposedly replacing smbfs.

Doeas anybody have a suggestion as to how I can mount properly CIFS shares and somehow speed up the time it takes for the files to show up?


If anybody is interested, here's my fstab which actually mount the shares:
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
//DiskStation/music on /media/music type cifs (rw,mand)
//DiskStation/photo on /media/photo type cifs (rw,mand)
//DiskStation/video on /media/video type cifs (rw,mand)
//DiskStation/documents on /media/documents type cifs (rw,mand)
//DiskStation/install on /media/install type cifs (rw,mand)
//DiskStation/public on /media/public type cifs (rw,mand)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

however, the shares appear to be empty!?!
If I mount via fstab it seems the files never appear?

Anybody else having the same problem? 

With best regards,
Michael Larsen

---

### Post by dstew on 2007-03-01
Once I had a similar problem. The share mounted but the folder appeared empty. The problem turned out to be a file name in the share that had a strange characher in it, I think it was a "trademark" symbol (you know, a little Tm). When I renamed the file without the Tm character, all the files showed up. I never found anything on the web or forums about this behavior. It was in samba though, not in cifs, but that is all I can think of.

---

### Post by juergi on 2007-04-02
Try to add
unix extensions=no
to the global section in 
/usr/syno/etc/smb.conf

Best regards,
juergen

---

