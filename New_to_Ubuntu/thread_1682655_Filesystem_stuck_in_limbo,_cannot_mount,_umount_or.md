---
title: "Filesystem stuck in limbo, cannot mount, umount or fsck"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by rohedin on 2011-02-06
Hi,
I'm having some major trouble trying to rescue a broken Xubuntu 10.10 installation. The startup fails shortly after GRUB, and bails to BusyBox with the message:
```

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
```

I assumed this was due to something getting corrupt, the disk has had quite a few failed sectors in the past (a Maxtor drive in an 8 year old Dell, need I say more?). I booted up a live CD to attempt to run a fsck on it, but fsck refused to start complaining the device or resource was busy. The partition (/dev/sda1)was however unmounted, forcing an unmount just said that the device was not mounted. I used various command to check, but apparently no process was using the disk either.

At the very least I thought I'd try to rescue the documents off the disk, so I tried to mount it; however the mount command failed, as there was no entry for /dev/sda1 in /etc/fstab. So I manually edited in an entry for it, but this just caused mount to hang endlessly without giving any output.

I would assume that the hard disk had physically failed or the partition was completely wrecked, but GRUB has no trouble mounting it and displaying the boot menu, it only fails when the kernel tries to mount it. GParted also correctly reports the disk usage as being about 5GB/30GB (GParted also encounters similar problems if I try to use it to check the disk).

Perhaps some kind of important descriptor in the filesystem has corrupted and is incorrectly reporting the state/usage? I'm not very clued up with filesystems, so does anybody know a way of at least running fsck or mounting this partition?

(If this is the wrong forum, please tell me, I haven't used this website in a few years)

---

### Post by rohedin on 2011-02-06
Has nobody experienced anything like this before? I can't find any helpful info at all.

---

