---
title: "Updating RAMFS Help"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Syndacate on 2009-12-20
Hey,

I have a Macbook Pro (5,3) and am running Karmic on it.

I'm following [THIS]("https://help.ubuntu.com/community/MacBookPro5-3/Karmic") URL.

Anyway, I got to the part about swapping my function keys where you have to update the RAMFS image.  I did it, with the "options" file added to /etc/modprobe.d/ directory by adding the following options to the "options" file to invert the function keys:
```
options hid_apple fnmode=2
```

Anwyays, then I restart and I get a kernel panic for not being able to sync or something to that effect (the only kernel panic I ever get under Linux).

I used the following command to update:
```
sudo update-initramfs -u -v -k `uname -r`
```

So since I updated from the -14 kernel to the -16 kernel I was able to start Ubuntu under the -14 kernel/image, but I don't know how to use the above command (now that I've deleted the "options" file) to update the image for the -16 kernel, as that's what I'd like to use.  The above command, if I understand it correctly will update the current kernel's RAMFS image in use, no?

How do I re-image the one for my -16 kernel so I can boot back, again.

Thanks!

- Greg

---

### Post by Syndacate on 2009-12-20
Hey,

Nevermind, peeps, I got it.

According to the man pages:
Without specifying the kernel version (which is produced by the `uname -r` variable) and the -k option for the script it will default to the latest kernel installed.

So it's just:
```
sudo update-initramfs -u -v
```

It will re-generate the RAMFS image for the latest kernel, everything works again.

Thanks, anyways, guys.

- Greg

---

