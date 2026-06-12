---
title: "Path to a NFS share in bash"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by xeo_pt on 2007-07-13
Hi,
I need to access a NFS share in another computer (Linux) from the bash shell,
but I can't find where Ubuntu mount the NFS.

With Gnome it works great but I need to access by a script.

Thanks in advance.

---

### Post by Mr. C. on 2007-07-13
On the remote system, go to the command line and look at the output from the command:

```
mount
```

If that does not help you, show the output and indicate what server / file system you expect to see.

MrC

---

### Post by xeo_pt on 2007-07-14
The outpput ot [FONT="Courier New"]mount:[/FONT]
> /dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda on /media/cdrom0 type iso9660 (rw,noexec,nosuid,nodev,user=ad)


I think what I need is[FONT="Courier New"] nfsd on /proc/fs/nfsd type nfsd (rw)[/FONT]

my question is where is the nfsd mounted?

Thanks for you help.

---

### Post by Mr. C. on 2007-07-14
I see no NFS mounted file system on your system.

You must explicitly take action to mount a remote file system in the location you desire on the current machine.  It will then be located where you specified, as in :
```

mount -t nfs mynfsserver:/path/to/exported/directory  /mnt/myremotefiles
```

Ignore the /proc stuff.

What action have you taken to mount the remote file system ?

MrC

---

### Post by xeo_pt on 2007-07-14
Brilliant!

I use to mount the remote fs with gnome!

but this way is much better.

Thanks a lot, buddy.=D>

---

