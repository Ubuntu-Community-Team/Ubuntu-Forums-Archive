---
title: "How to copy to external hard disk???"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by yizsa on 2009-05-24
Hi,
I wanted to copy some files to an external hard disk, but was not allowed.
Under Properties>Permissions>Owner: root
and it says '**not the owner, can't change these permissions**.'
I tried the **chmod** command, but it gave another message: read-only file system.
I'm not sure if I'm doing anything wrong?

Please help.

---

### Post by Boondoklife on 2009-05-24
I assume this is a firewire or usb dirve correct?
plug in the drive and then post the output of```
mount
```

---

### Post by yizsa on 2009-05-24
Hi,

here's what i got...

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/FreeAgent Drive type ntfs (rw,nosuid,nodev,umask=222,utf8)

---

### Post by halitech on 2009-05-24
you need to change ownership as well

```
sudo chown -R username:username /dev/sdb1
```

change username to your username

---

### Post by yizsa on 2009-05-24
Hi,

I tried that, no error msg on terminal.
but when i try to copy files into the external hard disk again, it still doesn't work.
pops up a msg: [B]You do not have permissions to write to this folder.
[/B] Sorry I'm quite a noob. 
I tried to umount and mount again, but still can't copy.
Am I doing something wrong?

---

### Post by halitech on 2009-05-24
try changing /dev/sdb1 to ```
/media/FreeAgent\ Drive
```

note: make sure you include the \ after FreeAgent so it sees the space in the name. then do the chmod command as well

---

### Post by yizsa on 2009-05-24
I got this instead:
chown: changing ownership of `/media/FreeAgent Drive': Read-only file system

??

---

### Post by halitech on 2009-05-25
I just realized, your external is NTFS, chown and chmod aren't going to work as ntfs don't support unix file permissions. Have to handle write permissions differently but can't think of it right now.

---

### Post by LiamWilson on 2009-05-25
You could try 
```
sudo nautilus
``` and then finding your drive and then changing the permissions.

---

### Post by halitech on 2009-05-25
don't think that will work either (also you shouldn't use sudo for graphical apps but gksu)

check out the info here
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

