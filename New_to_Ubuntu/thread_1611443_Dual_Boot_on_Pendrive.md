---
title: "Dual Boot on Pendrive"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by k33bz on 2010-11-01
Ok, here soon I will be getting my 16Gb thumbdrive. (already ordered, just waiting on mail).

What I want to do is dual boot BT3 and BT4 with persistence onto this thumbdrive. How do I go about doing this, the simple way. I know there is Unetbootin, however to my knowledge I cant make it dual boot or make it persistent with that program.

Figure this be the right place to ask since BT4 is based on ubuntu 8.04

---

### Post by wilee-nilee on 2010-11-01
> **k33bz said:**
> Ok, here soon I will be getting my 16Gb thumbdrive. (already ordered, just waiting on mail).

What I want to do is dual boot BT3 and BT4 with persistence onto this thumbdrive. How do I go about doing this, the simple way. I know there is Unetbootin, however to my knowledge I cant make it dual boot or make it persistent with that program.

Figure this be the right place to ask since BT4 is based on ubuntu 8.04

With 16 gigs just do full installs of both. Not sure what BT3 or BT4 is but if it unpacks to less the 3 gigs like hardy then fully installed might be a better option.

Pendrivelinux has a multiboot I use it but the persistent can only be for one distro.
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

---

### Post by k33bz on 2010-11-01
BackTrack3 and BackTrack4

---

### Post by k33bz on 2010-11-01
> **wilee-nilee said:**
> With 16 gigs just do full installs of both. Not sure what BT3 or BT4 is but if it unpacks to less the 3 gigs like hardy then fully installed might be a better option.

Pendrivelinux has a multiboot I use it but the persistent can only be for one distro.
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

was noticing that pendrivelinux uses .exe files. Will these run in WINE?

---

### Post by wilee-nilee on 2010-11-01
> **k33bz said:**
> was noticing that pendrivelinux uses .exe files. Will these run in WINE?

That I don't know but as a alternative you could download this legit XP iso and run it in a virtual and load the thumb. You just need the Oracle off the web version puel.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

All MS releases have a free use time so I think this is well within in legal issues.

I like this multi boot ISO setup it has a grub menu and a grub.list even though it is grub2, you can add any distro to it if you know how the grub.menu should look, I used maverick on it before release.

The same thing can be done with a grub2 install but I don't know the method, if you look through oldfreds posts though he mentions this at times.

---

### Post by Keiran230 on 2011-02-21
I haven't done a dual boot on my USB drive, but I can at least tell you how to get persistence working. After copying the CD filesystem over to a FAT32 partition using Unetbootin or rsync (Backtrack's offensive security site has a video on that [[COLOR="Red"]here[/COLOR]]("http://www.offensive-security.com/backtrack/backtrack-4-persistent-usb-install-video/")) you simply need to create another EXT3 partition, then change its label to casper-rw. Backtrack 4's menu.lst already knows how to handle persistence partitions if they're named casper-rw, and auto-mounts them appropriately.

---

