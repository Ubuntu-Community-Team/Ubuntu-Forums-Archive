---
title: "Clean Install  vs. Upgrade -- Lucid to Maverick"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Nodaki on 2010-10-13
In the old days--upgrading Windows versions was frequently a giant mess.  A much buggier and genuinely slower machine was the result.  A clean install was always favored.

Does this old perception hold true for Ubuntu distro versions?

In my own experience: I have been very pleased with upgrading and I believe I started doing so about 4 versions ago on an HP 8510p without a major issue.

---

### Post by jtarin on 2010-10-13
That perception holds true for any Operating System. This is why it is always suggested to make  seperate partitions for /and home. There are many other partition schemes but this is the most common and as you learn Linux you will come to understand what directories are important to you...personally.

---

### Post by k3lt01 on 2010-10-13
A clean install, if you have separate / and /home partitions, is always preferable. I have 2 installs on this machine (the laptop listed in my signature), the one I am using now is slower than it was yesterday and it was an upgrade (from 9.10 to 10.04 to 10.10). The other install is a fresh install and it is lightening fast even on this old machine.

To be fair to the upgraded install I do need to do some cleaning up and that will bring it back to life.

---

### Post by clickwir on 2010-10-13
> **k3lt01 said:**
> To be fair to the upgraded install I do need to do some cleaning up and that will bring it back to life.

What kind of cleaning up do you do/suggest? 

I've upgraded and had a heck of a time with the RADEON drivers, wouldn't load without passing RADEON.MODESET=0 at boot. Switched to FGLRX and it's much better. Also, sound is hit or miss. Some apps work. Some don't. This boot, nothing works with sound. Next boot, it might. But that's a whole other thread I won't get into here.

---

### Post by sgosnell on 2010-10-13
I have a separate /home partition, but I still prefer to upgrade.  I have a lot of extra packages installed, and remembering all of them, then installing them, is a real pain.  The upgrade to 10.10 recognized all of them, and upgraded those which were available.  It took awhile, but far less time than it would have taken to do a complete fresh install and then install all the packages from scratch.

---

### Post by john newbuntu on 2010-10-14
I did a new install of 10.10 and an upgrade on 2 separate machines.  Both went just fine and are fast too.  Yes there are some minor glitches with 10.10. I have been upgrading for the last 3 versions without prolems.

For a new install, what I typically do is to first install all upgrades as recommended.  I have all my extra applications in a file such as this one:
```
bleachbit          install
build-essential  install
chkrootkit        install
```

and run a batch script which then installs all my extra apps using the "dselect" method.  The script also modifies any system files per my requirement (example: enabling ufw, modifying /etc/default/grub, changing termcap in xterm, disable/enable rc or init scripts etc). Mind you, I have a separate /home partition.

You can generate your extra package file by doing a diff between the current package list and the old one.  You will have to get rid of the older versions of different packages though.

All these just make my new install faster keeping all my apps. I always backup/tar my working install.  It's priceless.  If something goes bad, I can always restore it and move on.

---

### Post by GabrielYYZ on 2010-10-14
i did an upgrade from 10.04 to 10.10 and it went smoothly. i use the ubuntu tweak feature that lets you clean the cache, unused packages and config files and, occasionally, bleachbit (like every 2-3 days) to keep it reasonably nimble. 

i have no complaints for now, everything's running a-ok.

---

### Post by k3lt01 on 2010-10-14
> **clickwir said:**
> What kind of cleaning up do you do/suggest? 
I follow [this guide]("http://ubuntuforums.org/showthread.php?t=140920") and it works a treat for cleaning the system WITHOUT having to add anything NON-Ubuntu to the system. Things like Ubuntu Tweak are fine if you want to add more bloat to your system in order to remove a small amount of material.

Now I will wait patiently for the flaming.

> **clickwir said:**
> I've upgraded and had a heck of a time with the RADEON drivers, wouldn't load without passing RADEON.MODESET=0 at boot. Switched to FGLRX and it's much better. Also, sound is hit or miss. Some apps work. Some don't. This boot, nothing works with sound. Next boot, it might. But that's a whole other thread I won't get into here. Without knowing your system anything I suggest would be a guess at best.

---

### Post by GabrielYYZ on 2010-10-14
> **k3lt01 said:**
> I follow [this guide]("http://ubuntuforums.org/showthread.php?t=140920") and it works a treat for cleaning the system WITHOUT having to add anything NON-Ubuntu to the system. Things like Ubuntu Tweak are fine if you want to add more bloat to your system in order to remove a small amount of material.

Now I will wait patiently for the flaming.

 Without knowing your system anything I suggest would be a guess at best.

my system is not bloated! *shakes fist* :P 

i find Ubuntu Tweak to be quite useful for random stuff, but i agree that installing it just for the removing stuff feature is not a wise thing to do. 

btw, that guide = awesome. localepurge is quite nice... :)

---

### Post by migs73 on 2010-10-14
I have a kind of cheat, I do a fresh install, but have two / partitions, one for new version and one for old. I can run the new one till I have everything the way I need it, but still have the older one if I have forgotten something.
Both of course share /home, so my settings are the same.

---

### Post by Jakiejake on 2010-10-14
> **Nodaki said:**
> In the old days--upgrading Windows versions was frequently a giant mess.  A much buggier and genuinely slower machine was the result.  A clean install was always favored.

Does this old perception hold true for Ubuntu distro versions?

In my own experience: I have been very pleased with upgrading and I believe I started doing so about 4 versions ago on an HP 8510p without a major issue.

I did a full clean install of 10.10
And I'm glad I did
If you had any problems in previous versions it's gonna be a fresh start!

---

### Post by k3lt01 on 2010-10-14
> **GabrielYYZ said:**
> my system is not bloated! *shakes fist* :P Didn't take long:guitar: lol

> **GabrielYYZ said:**
> i find Ubuntu Tweak to be quite useful for random stuff, but i agree that installing it just for the removing stuff feature is not a wise thing to do. Despite popular, and incorrect, opinion I don't actually have a problem with UT. I just have a problem with people saying its a cure all or the best thing since sliced bread.

> **GabrielYYZ said:**
> btw, that guide = awesome. localepurge is quite nice... :)Yep, localepurge is a good thing, so is deborphan. I find the way the guide is set out makes it pretty easy for anyone to learn basic maintenance of their Ubuntu system.

---

