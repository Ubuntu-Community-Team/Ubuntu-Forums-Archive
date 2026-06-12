---
title: "Graphic System Tree"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by illumin8 on 2009-05-04
Has anyone seen or heard of either a graphic representation of either ubuntu
or a debian based system? More specifically, Kernel, Shell, Programs, etc.

I want to start familiarizing myself with some of the more common core programs, why they are chosen, how they work, and how to play with them.

Slackware has a decent from the ground up manual, but i havent seen anything as comprehensive for a debian based system.

That seems to be the most challenging part...not learning the stuff, but finding the stuff to learn.

---

### Post by hw-tph on 2009-05-04
Debian has excellent documentation, most of which you can find [here]("http://debian.org/doc/") or install from your package manager. I suggest you start out with the Debian FAQ and then move on to other topics. The Debian Reference manual is always a good read too.

Most - but not all - of the stuff in the Debian manuals applies to the Ubuntu collection of distributions.

---

### Post by cariboo on 2009-05-04
You may want to have a look at [The Linux Documentation Project]("http://tldp.org/"). there is quite a bit of documentation available.

---

### Post by Didius Falco on 2009-05-04
This is a pretty good explanation of the structure:

[http://knol.google.com/k/manoj-ap/linux-and-shell-commands/3bx1ymwndxj4/33#](http://knol.google.com/k/manoj-ap/linux-and-shell-commands/3bx1ymwndxj4/33#)

This thread is a treasure trove of resources:

[http://ubuntuforums.org/showthread.php?t=1148076](http://ubuntuforums.org/showthread.php?t=1148076)

And don't forget the **man** pages.

I hope this helps..

---

### Post by illumin8 on 2009-05-04
Generous responses.
Thankyou.
Lots of good info here.

---

### Post by Alterax on 2009-05-04
> **hw-tph said:**
> Debian has excellent documentation, most of which you can find [here]("http://debian.org/doc/") or install from your package manager. I suggest you start out with the Debian FAQ and then move on to other topics. The Debian Reference manual is always a good read too.

Most - but not all - of the stuff in the Debian manuals applies to the Ubuntu collection of distributions.

Couldn't have put it better myself.  The Debian documentation's really good.
Here's the highlights though:

/boot is where your kernel and bootloader configs go.
/lib is system libraries.
/home is users' home directories
/var is data that changes a lot, like web content, spooled data, databases.  Think VARiable or VARies and you've got it.
/usr/bin and /bin are binary files.  /usr/local/bin is a place to put binary programs that you create.
/sbin/ and /usr/sbin are system binaries used for administrative tasks.  Think System BINaries.
/etc/ is trickier; it's configuration files and startup scripts.
/dev/ is System Devices.  In Linux, everything from your drives to your keyboard is considered a file.  /dev/ is where the system keeps these files that represent the DEVices.
/mnt/ is for static MouNT points.  You might want to make an always-on link to a file share on another system.  Do that here.
/media/ is a bit newer; it's for media that changes more often, like mounting USB sticks, CD-ROMS, and temporary file shares on other computers.
/proc/ doesn't really exist except in RAM.  It's the data of your currently running PROCesses.
/sys/ is like PROC in that it only exists in RAM.  It's where your system data (like kernel settings currently in use) are accessed.
/opt/ is OPTIONAL.  It's a leftover from (if I remember right) SystemV Unix that was kept for compatibility reasons.  Since there's nothing that "should" be in here, I use it as a space for developing programs and keeping a subversion repository.  Other uses are for commercial software or backups; it's pretty much your choice.

oh, and HW-TPH:

Off-topic but I couldn't help but notice the sphynx picture in your avatar.  Handsome kitty; I have one curled up at my side too!

---

