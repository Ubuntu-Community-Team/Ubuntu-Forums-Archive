---
title: "Ubuntu won't mount file system"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by madjackrogers on 2009-12-30
I originally posted this in another section, but I realized it's probably more appropriate here, as I know very little about what I'm doing.

So, I was trying to get that annoying beep to go away in firefox/pidgin when I backspaced things, and I think I missed something up. I added a line of code into /etc/gtk-2.0/im-multipress.conf, and now my system won't boot.

This could also be that I deleted some extra entries from GRUB via menu.lst so I only had the ones I needed.

My symptoms include:
when I try to boot in regular or recovery mode, the ubuntu 8.04 load screen shows up (I relatively recently upgraded from 8.04 to 8.10, then to 9.04, then to 9.10) the orange bar goes back and forth for a while, then it gives me a bunch of errors and dumps me out
as root.  specifically, it says that it couldn't mount the devices, apparently.  general error mounting filesystems.

I tried changing the file multipress.conf back to its original form using the nano command, but it said I couldn't because it was read only, even when I tried using sudo.

I honestly have no idea what I've done or what's going on here.  Can anyone help?

I've tried fsck, that came back clean.

---

