---
title: "Ubuntu updates destroy boot directory"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by Scottydogg on 2010-11-12
I'm requesting speculation here.
Very often if I allow update manager to install new updates, my computer fails to mount the boot directory and cannot be fixed (at least by me!).
Recently updates caused Compiz to fail. 

I couldn't find a way to fix it, so did a fresh install. (I like compiz)
installed all my favorite programs using apt-get, no problem.
ran some package manager updates, no problem.
The second set of security updates crashed my computer. 
I don't remember what was in them, but there were definitely no kernel updates or anything I would expect to be messing with my boot directory.
If I suspend all updates, things seem to go fine; it's when I allow update manager to run. Coincidence?
Is my hard drive failing?
How would I be able to tell?

In advance: thanks to all the hard working people who:
A) make this my favorite operating system
B) help people like me who don't know how to solve a problem that can't be fixed with a right-click.

---

### Post by garvinrick4 on 2010-11-12
Tell the people what kind of machine you are using and what version of Ubuntu you are running.

---

### Post by freshmeatz on 2010-11-12
Yeah I just checked and I could update about 180megs on this 10.10 64bit version, but some is kernel headers for amd64 etc, compiz updates, cups,so forth, almost afraid to do so. maybe Ill go one package at a time if possible to eliminate issues. :popcorn:  
I/O errors in /var/log/messages indicates that something is wrong with the hard disk and it may be failing.

or you could try smartctl and check your drive

smartctl -d ata -H /dev/sdb  "dont forget to change your drive <sdb> etc"

if you dont have it then

sudo apt-get install smartmontools

---

