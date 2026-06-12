---
title: "Disks doubling in 'Places'"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by lucasl on 2009-11-08
Hi,
I have a modified fstab for easy mounting and to limit some drives to root access. After updating to 9.10, I've noticed that the drives in fstab which I've specified as 'user' appear twice (but not the nouser ones), as if there is one entry for the fstab list and one for Ubuntu's autodetection.

Not a huge problem, but it bugs me.:)

Any ideas on how to remedy this?
Thanks!

---

### Post by ikisham on 2009-11-08
I'm not in Ubuntu now but you could look at /etc/mtab and compare with /etc/fstab. Maybe Ubuntu is mounting the same partition twice in different places, one in mtab and one in fstab. Then perhaps you could edit fstab to mount in the same place as mtab.

---

### Post by lucasl on 2009-11-08
Well that's the strange thing, ikisham, this happens when they aren't mounted (and doesn't stop when they are)!
In fact, looking at one which is mounted now, the tooltip of one says "209GB Filesystem" and the other "Mount Win7".
The drive itself doesn't have a label, so it looks like the one that says Win7 must be from fstab (it's set to mount to /media/Win7).

---

### Post by ikisham on 2009-11-08
First, the Ubuntu detected is the "209 GB Filesystem". The other is you line in fstab.
Looking at my installation I see that any partition that isn't auto-mounted don't figure in it, that's why when you added that line it started to figure twice. So I guess you can safely remove that custom line there (make a back up of the file, just in case).
FYI, as you can see if you click on the "209 GB Filesystem", it asks for the password to mount it.

I heard that Karmic uses a different system for mounting, I think it's based on udev and not fstab (if you want to try to figure it by yourself, try looking at /lib/udev/rules.d). I have a partition auto-mounted at boot time but I set it during the installation and so it figures in fstab.

---

