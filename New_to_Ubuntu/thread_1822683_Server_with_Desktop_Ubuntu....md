---
title: "Server with Desktop Ubuntu...?"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by SilverJS on 2011-08-10
Guys,

Built this box a month ago, with the express purpose of running FreeNAS or FreeBSD on it, for ZFS.  Essentially :

Asus M4A88T-M/USB3
Athlon II X2 255
8 Gigs ECC RAM DDR3 1333
7 X Hitachi 3TB hard drives
1 X WD 500GB System drive (not used with FreeNAS right now)

Plan was to use ZFS, with 6 drives in a RAIDZ2 array with one hot spare.  Thing is, FreeNAS has started acting up lately and I am considering switching to Ubuntu, either server or desktop.

Honestly, I'm not too concerned about speed - more reliability.  This box is only for back-ups (I already have a file server - the contents of which also need backing up - for streaming my media), but I do need it to be able to run 24/7.  That being said, I would appreciate the functionality of a full desktop, especially when setting it up.  My questions :

1.  Is it possible to set up the Desktop version of Ubuntu, to just use my 7 3TB drives in a RAID6 array, with one hot spare, using the 500G drive as a system drive?
2.  Is it possible to add a desktop to the Server version of Ubuntu?
3.  Of the two above, which do you recommend?
4.  Either way, will I be able to run this box headless, and administer it via web or some other remote means?
5.  Can I set up e-mail alerting with that too?

That would answer all of my modest needs.  I understand there might be other Linux distros out there who could also do this, but I've fiddled around a bit with Ubuntu and find it to be the most polished, easy-to-use and complete out there.

Thanks in advance!

---

### Post by Jagoly on 2011-08-11
Yes, you could run the desktop version of ubuntu. However, the server edition would probably be much easier. It's extremely simple to use.

Setting up a raid is also easier in ubuntu server.
Running the desktop editon headless is possible, but a lot harder than just running a simple ssh connection.

I'm not a server pro, but I have quite happily set up a micro server with apache and samba, with a raid1 array with ubuntu server. I can't imagine it being any simpler.

And zfs can be configure from an external ppa too, but I've never used it.

PS: I'm not sure this is absolute beginner talk ;-)

---

