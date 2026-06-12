---
title: "External USB NTFS Drives with Ubuntu 9.10"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by pablolie on 2009-11-27
Holy Schmoly! I upgraded my music server (which runs Squeezeboxserver 7.4.1) to Ubuntu 9.10, and I must say it was quite awful to find out that, the installation that had worked flawlessly from Ubuntu 7.10 all the way to 9.04 suddenly did not work anymore. The only change was the install (clean) of 9.10, replacing 9.04.

After installing Squeezeboxserver in 9.10, it (Squeezeboxserver 7.4.1) would no longer see the external USB drive that had always been there for years. Yikes. 

I came to this forum and there are *SO* many threads about this topic that
(a) it is very hard to discern what the up to date information is
(b) there is a real issue there for a high number of users

If editing the fstab is really the answer that the Ubuntu development community wants users to go for, fine, but at least there should be a better, up to date guide or wiki somewhere that instills confidence. 

The worst thing I can say about this is that I had to try several things that did not work, and then, at some point in time, upon restarting, things worked. But I can truly not say exactly why. And I am quite computer versed. 

For reference, my fstab entry now reads
# Entry for /dev/sdb1 :
UUID=28D89082D8904FC4 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

Seemingly changed from 
# /windows was on /dev/sdb1 during installation
UUID=28D89082D8904FC4 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

which now resides on a file called fstab.pre.ntfs-config, which makes me assume that ntfs-config did a magicn change and that *that* is what users ought to be going for. I am not sure this is truly consistently communicated around here. Mind you, the screens I got while doing that looked nothing like described in the thread that lead me to fire up the NTFS configuration tool (all the latter offered to me was to click 2 boxes for write permission, that was *it*). Weird.

But given how many discussions there are on this topic, and how high the signal to noise ratio is (or so it seemed to me), I wanted to highlight this.

There has to be a better way!

---

### Post by cariboo on 2009-11-28
I have to ask, why upgrade if everything works the way it ahould?

---

