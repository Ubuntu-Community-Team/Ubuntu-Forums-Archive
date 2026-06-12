---
title: "Jaunty kernel 2.6.28-13generic crashes at boot! HELP!!"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-07-12
Hey guys,

I'm on Ubuntu 9.04 64-bit, and I had my computer running since yesterday because I was downloading a large torrent. When I restarted it this morning, I got the following error messages at bootup:

> Starting up ...
[    0.028357] ACPI: Aborted because junk in compressed archive.
[    2.764838] Invalid compressed format (err=1)
[    2.769929] Kernel panic - not syncing: VFS: Unable to mount -root fs on unknown-block(0,0]

It hangs from there. No boot possible. Scared the living daylights outta me (still does).

It took me some time to figure out, but when I use GRUB to load an old Kernel - the prvious one: kernel 2.6.28-12generic - it boots without a problem (I only had to reinstall my Nvidia graphics driver on that one).

It seems like something f***ed up the newer kernel - is there a way to rebuild it, restore it, repair it? My poor ole heart can't take this kind of pressure! :-(((

I thought some hardware might be broken (most likely the hard disk), but I'm not sure about that. I made backups of all my data, so that's safe for now, bit I'd love to go back to regular work with this PC...

Thanks so much!!

---

### Post by AndThenWhat on 2009-07-12
It just means your hardware doesn't like the new kernel. All you have to do is choose the old one during boot.

---

### Post by earthpigg on 2009-07-12
no need to rebuild the newest kernel or anything like that -- your computer was working fine for "X" months with the old one, so stick to it :D

this is exactly why ubuntu keeps the old kernel's around even when it updates to a newer one.

-11 kernel works fine on your setup, and thousands of others with a similar setup.
-12 kernel does not work in your setup, and thousands of others with a similar setup.

in theory, -13 will work fine for you.... but inevitably *not* work with a whole new setup that thousands of people have. those people will stick with -12 and hopefully, -14 will work for them.

hopefully, each time a new kernel doesn't work with a bunch of people... the 'bunch' is a smaller and smaller number as time progresses.

and so on, as the persuit of perfection continues.


if you want to do your part and report that this linux kernel does not work with your system:

> ubuntu-bug -p linux

be sure to include exactly which Linux Kernel it is that does not work on your system. example: kernel 2.6.28-13generic

---

### Post by The Bright Side on 2009-07-12
Okay, that's a relief. Thanks guys. I will report it, too.
One more question: how can I get Ubuntu to boot with the working kernel by default? Right now, I always have to manually select the old Kernel (i.e. -12) from GRUB at bootup, otherwise, it will try to load the new kernel and crash.

Thanks!
M.

---

### Post by earthpigg on 2009-07-12
2 options to change the default kernel used to boot:

1) manually change /boot/grub/menu.lst. this is the hard way.

2) easy way:

```
sudo apt-get install startupmanager
```

system -> administration -> startup-manager -> default operating system -> pick yer kernel

edit: dont play around to much in startupmanager, it isn't hard to shoot yourself in the foot working with that stuff.

---

### Post by The Bright Side on 2009-07-12
Thanks!! Works like a charm.

---

