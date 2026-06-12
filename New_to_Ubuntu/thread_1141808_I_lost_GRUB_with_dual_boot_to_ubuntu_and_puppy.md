---
title: "I lost GRUB with dual boot to ubuntu and puppy"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by fredfelter on 2009-04-28
I have posted this on the Puppy forum also but find it is much less active than this fabulous one.

I am trying to put Ubuntu and Puppy as a dual boot on a second HD on my Thinkpad T22. The Ubuntu Hardy install went fine but when I added Puppy 4.2 "full install" to a fourth primary partition on the drive Puppy took over the bootup menu; such that Ubuntu GRUB starts to load but within seconds the Puppy one supplants it. Now when I click on the Ubuntu boot up choice it says "no file found". Puppy boots fine.

What I would prefer would be to have the Ubuntu GRUB as the only boot up menu. Being a noob I can't understand the couple of suggestions I found on how to solve this problem on the web. Is there a straightforward way to accomplish this, even if I have to reinstall one or both OSs ?

Thanks

---

### Post by supererki on 2009-04-28
no you just have to reinstall GRUB.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

i think this might help you.

---

### Post by flyingsliverfin on 2009-04-28
well, if you don't like the complicated way just install ubuntu after puppy!

---

### Post by egalvan on 2009-04-28
I triple-boot XP, Hardy & Puppy 4.2
(oops, this NOT the "Full Install" for Puppy, 
but the "Frugal Install".
Frugal is MUCH easier to up-date, so i use it.)

Here is some (hopefully) relevant portion of the info...

```
## END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider,
# added to separate the menu items below from the Debian
# ones above.
title		Other *nix OS's:
root

#   original puppy frugal install, no longer used, does not exist
# title		Puppy Linux 4.00, no longer used, does not exist
# rootnoverify	(hd0,5)
# kernel	/vmlinuz root=/dev/ram0 pmedia=idehd
# initrd	/initrd.gz

#   previous puppy frugal install, using folder, no longer used, still exists
#title		Puppy 4.11
#rootnoverify	(hd0,5)
#kernel		/puppy_411/vmlinuz root=/dev/ram0 pmedia=idehd psubdir=puppy_411
## pfix=ram	if used, will not load "save files"
#initrd		/puppy_411/initrd.gz

#   current puppy frugal install, using folder
title		Puppy 4.12, using 411 "save files"
rootnoverify	(hd0,5)
kernel		/puppy_412/vmlinuz root=/dev/ram0 pmedia=idehd psubdir=puppy_412
# pfix=ram	if used, will not load "save files"
initrd		/puppy_412/initrd.gz
```

---

### Post by fredfelter on 2009-04-28
I never know whether it's a good idea to bump my topic by offering a thanks but I do appreciate the info that I got from you 3; supererki, flyingsliverfin and egalvan. That should be doable even by me.

---

