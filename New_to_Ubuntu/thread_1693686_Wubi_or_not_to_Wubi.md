---
title: "Wubi or not to Wubi"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by TopgunB on 2011-02-23
I have had Ubuntu 10.10 Gnome installed under  Win 7 using Wubi on my computer for 2 weeks now and I am absolutely loving learning about it. It is working well and I can do most things I need to do. Is there any advantage to partitioning my hard drive and installing it as a dual boot in that manner rather than via Wubi??

---

### Post by aeiah on 2011-02-23
someone'll probably chime in with some proper info, but since ive never used wubi ill give my point of view: using proper partitions may help if things go very wrong at some point down the line, or if you need to reinstall windows etc. 

having said that if you're happy with your system as it is, it isn't too important now. its probably not worth reinstalling things and messing with partitions at this stage. when you come to install a new version, perhaps consider doing it properly with partitions etc.

---

### Post by mastablasta on 2011-02-23
wubi might work a bit slower as it runs under windows. well it uses a virtualisation of sort.
OS under wubi can be of limited size (i think 30GB)
wubi creates one giant file if file get's corrupted you could lose everything you did in it.
does suspend/hibernate work under wubi? not sure about this one.
wubi also has some other minor limits and some of them have work arrounds.
 
for tinkering and such (trying out the OS) wubi is perfect. make sure you have certain updates disabled.

---

### Post by Bucky Ball on 2011-02-23
Yes! Is the short answer. 

* You are using Ubuntu basically as a Windows program and will not get full speed or features. 
* Wubi is really intended for trying Ubuntu for awhile and seeing if it fits your needs.
* You may not be able to access some of the available drivers, software and updates.
* You are not getting the full Ubuntu experience!

If you're liking it and learning heaps, you'll do more of the same with a full install and you'll learn something setting that up. If it's working well and you're liking it I say 'Go for it!', dual-boot or full install. Sounds like it's doing everything you need so why not the latter ... \\:D/

* Just reading the other posts that occurred while I was writing this one, as for partitions:

/ = where your Ubuntu lives - 20Gb is plenty;
/home = where your personal data and settings live - as big as you like;
/swap = the equivalent of a windows pagefile or swap - 2Gb fine, same as your installed RAM if you want to hibernate.

These are defaults in the partitioning section but you can create whatever partitions you like, fr instance:

/oldsock
/usedteabag

... etc. ;)

---

### Post by aeiah on 2011-02-23
from [wikipedia]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)"):
> Compared with a regular installation, a Wubi installation faces some limitations. Hibernation is not supported and the filesystem is more vulnerable to hard reboots. Also, if the Windows drive is unmounted uncleanly (most commonly because of a Windows crash), Ubuntu will not be able to mount the Windows drive and boot until Windows has successfully booted and shut down. If the Windows system cannot be booted after the crash, the user also cannot boot Ubuntu.
Performance related to hard-disk access is also slightly slower, more so if the disk image file is fragmented, on a Wubi install compared to a normal one.


so there you have it.

---

### Post by Bucky Ball on 2011-02-23
+1 aeiah, there you have it indeed ... ;)

---

### Post by listerdl on 2011-02-23
my opinion is not to wubi.

I like to be agnostic when it comes to OS's

I always think it is better for the OS to be operating in its native partition - but thats just my slighly philosphical take!

---

### Post by aeiah on 2011-02-23
yea it makes a lot of sense. if you use wubi and you mangle windows, you're gonna have a hard time getting into ubuntu.

---

### Post by sammiev on 2011-02-23
Tried both with good results but I prefer not to wubi. GL :)

---

### Post by Frogs Hair on 2011-02-23
I tried Ubuntu 9.10 via Wubi and without it I may not have tried Ubuntu as soon or maybe not at all . Wubi does have some advantage if plan to use Ubuntu from time to time or just want to check out the latest release .

I know 8 people using Wubi installations with Win 7 without any horror stories , but for their own reasons don't use Ubuntu as their main operating system. All the reasons to use a traditional dual boot have been outlined above.

For my own reasons I dual boot , but use Ubuntu most if the time.

---

### Post by Rubi1200 on 2011-02-23
If you are using Wubi, make sure to reference and read the following links:

[Wubi Guide]("https://wiki.ubuntu.com/WubiGuide")
For general information, including installation, uninstallation, and how to backup the root.disk

[Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198")
For Wubi issues and solutions

---

