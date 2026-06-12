---
title: "No startup"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by konsta82 on 2009-08-26
After last updates,9.04 wont start.
I got :
[I][B]udevadm trigger is not permitted while udev is unconfigured
gave up waiting for root device. common problems :
 -boot args (cat/proc/cmdline)
   -check rootdelay
   -check root
 -missing modules (cat/proc/modules; ls / dev

alert! /dev/disk/by-uuid/c835..... does not exist. droping to a shell
[/COLOR]
(initramfrs)[/B][/I]

I tried reinstalling grub with live cd but nothing changed.
This was dual boot system and windows is still working
What's wrong , please help !

---

### Post by alexlafreniere on 2009-08-26
Where are you seeing this message? In GRUB? Or after you select Ubuntu from GRUB?

---

### Post by konsta82 on 2009-08-26
it shows after I choose ubuntu
also there is 
[B]Busy box (ubuntu...) built in shell
ENter help for a list of commands[/B]

---

### Post by LewRockwell on 2009-08-26
> **konsta82 said:**
> After last updates,9.04 wont start.
I got :
[I][B]udevadm trigger is not permitted while udev is unconfigured
gave up waiting for root device. common problems :
 -boot args (cat/proc/cmdline)
   -check rootdelay
   -check root
 -missing modules (cat/proc/modules; ls / dev

alert! /dev/disk/by-uuid/c835..... does not exist. droping to a shell
[/COLOR]
(initramfrs)[/B][/I]

I tried reinstalling grub with live cd but nothing changed.
This was dual boot system and windows is still working
What's wrong , please help !

looks like you'll need to confirm your grub menu entry matches the kernel and uuid that you would like to boot

.

---

### Post by konsta82 on 2009-08-26
How should I do that ?
which command ?

---

### Post by LewRockwell on 2009-08-26
probably the first thing we would do if the unit was here would be to try using the Super Grub Disk to see if we could correct the trouble-call that way

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

otherwise you'll need to start checking things manually

.

---

### Post by konsta82 on 2009-08-26
looks like I'll need less time to reinstall 9.04 bcs I saw somewhere that my fstab is missing

---

### Post by LewRockwell on 2009-08-26
> **konsta82 said:**
> How should I do that ?
which command ?

```
alert! /dev/disk/by-uuid/c835..... does not exist. droping to a shell
```

here, grub is alerting you that /dev/disk/by-uuid/c835_blah_blah_blah doesn't exist

so with that clue you could check out the directory /dev/disk/by-uuid

and then you could check out your /boot/grub/menu.lst file to see which uuid and kernel it is telling grub to go to and boot up

you will also note here that we are purposely NOT giving you explicit keystroke-by-keystroke commands

these procedures are easily found in hundreds, if not thousands, of webpages strewn across the vast universe of the web

why reinvent the wheel

.

---

### Post by LewRockwell on 2009-08-26
> **konsta82 said:**
> looks like I'll need less time to reinstall 9.04 bcs I saw somewhere that my fstab is missing

where was this presented?

.

---

### Post by konsta82 on 2009-08-26
It shows when I enter mount disk

```
cannot read /etc/fstab ....
```

---

### Post by xzased on 2009-09-25
Check [this]("http://ubuntuforums.org/showthread.php?p=7995915") if you are still having probs.

---

