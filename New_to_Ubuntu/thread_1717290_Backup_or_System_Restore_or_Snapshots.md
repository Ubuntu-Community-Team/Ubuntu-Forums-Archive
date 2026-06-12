---
title: "Backup or System Restore or Snapshots?"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Zoriphus on 2011-03-29
Hey Everyone:

New to Linux and Ubuntu.  I have installed Ubuntu and everything appears to be working perfectly hardware-wise.

I know that in the Windows world, I learn by tinkering, and I am sure the same will apply here.

My question is this.  My machine is running perfectly right now.  Is there any way to take a backup, or some sort of system restore, or a snapshot of the way the system is now?  That way, when I start to make changes (and ultimately mess something up), I can easily revert back to the way the system was before I made the change?

I tried searching but didn't find exactly what I was looking for.  I suspect that I wasn't searching using the right words.  :)

Anyway, any thoughts?

Z

---

### Post by leclerc65 on 2011-03-29
I use Clonezilla to clone the whole system once, '/' and '/home' before installs and upgrades. I store data in a separate partition, back it up occasionally to an external HD using Grsync. Download Parted Magic and make a bootable CD or USB flash. It has the above programs and more.

---

### Post by n213978745 on 2011-03-29
There has a program called "remastersys" which works for both debian and ubuntu, it will create a live disc image, similar to system image in windows 7, by using whatever you install and have in your OS.

here is the link:
[http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)

---

### Post by Splat_NJ on 2011-04-19
Remasersys. I tried all the others I could find and this has worked for me every time.

---

