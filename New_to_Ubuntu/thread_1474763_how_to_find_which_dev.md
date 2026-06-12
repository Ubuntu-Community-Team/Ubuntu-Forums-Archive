---
title: "how to find which /dev/"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by chris200x9 on 2010-05-06
Hi I have a wedcam I found it with lsusb but I would like to know it's /dev/ adress i.e my cdrom is /dev/sr0.

---

### Post by quadproc on 2010-05-06
> **chris200x9 said:**
> Hi I have a wedcam I found it with lsusb but I would like to know it's /dev/ adress i.e my cdrom is /dev/sr0.
If your webcam is mounted then you can find it in the list produced by the ```
mount
``` command.  Please be advised that the /dev/xxx identifier can change from moment to moment; for example, if you unplug and replug the webcam then it may get assigned a different device identifier.  Likewise for rebooting.  The identifiers are assigned by the operating system, not by the I/O hardware.

quadproc

---

### Post by chris200x9 on 2010-05-06
> **quadproc said:**
> If your webcam is mounted then you can find it in the list produced by the ```
mount
``` command.  Please be advised that the /dev/xxx identifier can change from moment to moment; for example, if you unplug and replug the webcam then it may get assigned a different device identifier.  Likewise for rebooting.  The identifiers are assigned by the operating system, not by the I/O hardware.

quadproc
all I get is this:

```
[chris200x9@LinuxLappy ~]$ mount
/dev/sda6 on / type ext4 (rw)
udev on /dev type tmpfs (rw,nosuid,relatime,size=10240k,mode=755)
none on /proc type proc (rw,relatime)
none on /sys type sysfs (rw,relatime)
none on /dev/pts type devpts (rw)
none on /dev/shm type tmpfs (rw)
/dev/sda5 on /boot type ext2 (rw)
/dev/sda7 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/chris200x9/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris200x9)

```
also it's a built in webcan to my laptop.

---

### Post by Stéphane Scot on 2010-05-06
Look under /dev/v4l/  that's where my webcam[s] are sorted. v4l is Video4Linux so that makes sense...

---

### Post by quadproc on 2010-05-06
> **chris200x9 said:**
> all I get is this:

```
[chris200x9@LinuxLappy ~]$ mount
...

```also it's a built in webcan to my laptop.
OK, it isn't mounted.  Do you use the webcam in any applications?  If so, then running the app should mount it and you should then be able to see it in the mount list.

Another possibility is to look in the Places menu at the top of your screen.  There is a Computer selection in there that may show it.

quadproc

---

