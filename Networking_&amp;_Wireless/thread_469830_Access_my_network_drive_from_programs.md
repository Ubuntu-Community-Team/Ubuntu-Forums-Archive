---
title: "Access my network drive from programs?"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by tjoel99 on 2007-06-10
My documents and pictures are in my network drive which is mounted in Places.  

How do I access this network drive from programs such as web email (when sending attachments) and F-spot Photo manager?  The network drive doesn't show up.  Thank you.

---

### Post by Mr. C. on 2007-06-10
What is the output from the command line of:

```
mount
```

MrC

---

### Post by tjoel99 on 2007-06-10
Thank you.  Here is the output: 

family@cp:~$ mount
/dev/sdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
family@cp:~$

---

### Post by Mr. C. on 2007-06-11
Sorry for the late reply.

As suspected, you do not have your windows share mounted in the *nix sense (eg. into the file system).  You need to mount the windows share using the mount command, so that the share is visible within the file system.

See : [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

for a step by step.

MrC

---

### Post by tjoel99 on 2007-06-11
Thank you.  I'm kind of a newbie, but I will see if I know enough to be able to follow your instructions.

---

