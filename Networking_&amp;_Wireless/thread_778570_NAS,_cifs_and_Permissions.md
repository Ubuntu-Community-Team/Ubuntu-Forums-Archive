---
title: "NAS, cifs and Permissions"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by jcr1 on 2008-05-02
Hi all,

Have finally managed to mount my Freecom Network Drive NAS using cifs. Need a few issues clearing up. 

At the moment I am just mounting manually everytime until I have it all sorted. After log-out / log-in, obviously I need to re-mount, I can only do this after I perform an echo command into some file... really unsure what it does, I just did it as someone suggested it and it worked. It was something like:

echo 0 > /proc/fs?/Something/LinuxExtendedSomething

It seems I can only do that if I am root i.e. sudo -i

Why only as root?

Next once mounted, everytime I seem to have to chown the nas folder in /media (where it is mounted) so that I can read/write to it, otherwise permission denied to modify.

Why do I have to Chown everytime I mount.

Can these two items be resolved so I do not have to do them everytime I mount?

Also will permenantly mounting (in fstab) mean I won't have to echo and chown? even if I reboot and it automatically remounts?

Thanks in advance!

---

### Post by jcr1 on 2008-05-04
Bump...any one able to help? Cheers

---

### Post by jcr1 on 2008-05-06
Hellooooo?

Could really do with some input on this... :(

---

### Post by Unconscious on 2008-05-06
The mount under the media directory is handled by hotplug or some other system process (I dunno) which runs as root. Thus the directory directly under /media/ belongs to root. I have the same issue with my eSata and USB external disks. The top level directory on the device is always owned by root.

I don't know if there is any way to control this. I just create a directory under the top level directory on the device, which is owned by me. It makes the directory structure incrementally more complex, but I don't find that to be a huge problem.

---

### Post by Iowan on 2008-05-06
Check the link in my signature - it's getting a li'l dated (smbfs vs. cifs), but hopefully the basic information still holds.

---

### Post by jcr1 on 2008-05-07
thanks iowan. I will have another play, but I think your instructions are pretty muh what I have been doing already.

---

