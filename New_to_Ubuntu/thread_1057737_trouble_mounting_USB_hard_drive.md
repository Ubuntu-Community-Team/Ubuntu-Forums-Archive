---
title: "trouble mounting USB hard drive"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by linuxford on 2009-02-02
I have a PATA harddrive in a USB enclosure. 

Originally, I plugged it in and it automatically mounted it. I used "Places" to open up the harddrive contents. I then selected multiple files and dropped them on my Desktop (which effectively began a copy routine). While that was still running, and did another copy to some more files. This action seemed to lock up both copy processes for extended time. I then powered off the USB HDD device. And then repowered it on. Now when I try to mount it. It says

```
  Cannot mount volume.
  Unable to mount the volume.
```

I click the "Details" on the popup, and it says.

```
  mount: Stale NFS file handle.
```

I tried powering drive off. Rebooting, and then power USB HDD drive on. Same thing occurs. 

I don't know if there is an entry somewhere I have to modify? Or do I have to delete some sort of lock file? Or perhaps my drive is corrupted? Any suggestions are appreciated.

---

### Post by linuxford on 2009-02-02
Thanks for responding. That's interesting. Hmmm... I don't believe I have the NFS server loaded.

Here is the output of the mount command. I can't find which one it would be. It automounts to the /media/disk

```
rlee@lws01:~$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/gford/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rlee)
```

I was going to try after work tonite to put a different drive in the enclosure and see if I get the same problem.

By the way, this error also pops up after awhile if I don't close the first one.

```
Unable to mount 157.0 GB Media
Dbus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.
Possible causes include: the remote application did not send a reply, 
the message security policy blocked the reply, the reply timeout expired,
or the network connection was broken
```

Hopefully drive is not corrupted or something?

---

### Post by linuxford on 2009-02-03
> **linuxford said:**
> I was going to try after work tonite to put a different drive in the enclosure and see if I get the same problem.

This is interesting. I removed the problematic HDD out of the enclosure and put a different drive inside. They system recognizes this "NEW" drive in the enclosure.

I pulled the "NEW" working drive out, and put the "old" problematic drive back into the enclosure, and the "old" drive didn't work. From this, I deduce there is something about this drive that is the problem.

---

### Post by linuxford on 2009-02-04
Okay, heres what I think the deal is. When you are trying to use a hard-drive or any memory via the USB, it must be clean and free from errors, otherwise it may not be able to mount, and you will not be able to do anything with it. 

So what I did was I took the "bad" HDD out of the enclosure, and put it inside my computer (had to temporary disconnect my CDROM drive). I then tried to mount it, and as expected, it said that it was unable to mount. But now because it is connected directly to the computer, I ran the "fsck" command on the drive (ie. sudo fsck /dev/sdb1), and sure enough it had big problems. So after the errors were all cleaned up, I then put the drive back into the enclosure, and then plug it into the USB, and it mounts fine.

---

