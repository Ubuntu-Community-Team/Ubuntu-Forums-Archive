---
title: "Upgrading worries"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by mvalviar on 2009-03-22
Jaunty will be out in just a few weeks. I wanted to know how safe it will be to upgrade to it. I started with hardy tried to upgrade to intrepid. When the upgrade have finished there were lots of problems. I had to backup everything and reinstall hardy. It was a nightmare. After a few weeks I got my intrepid liveCD and installed it.

What is the safest way to upgrade? I mean some people say they reinstall in every release. That's every 6 months! Doesn't that defeat the purpose of using ubuntu instead of window$?

---

### Post by diablo75 on 2009-03-22
I know how you feel.  Upgrades for me are hit and miss between different systems (used by different people, and you don't always know what everybody does with their machines).

If I were you, I'd consider doing a re-install but do it in such a way to make future re-installs feel more like fast upgrades.  And the way you do that is, when installing and setting up your partitions, you create one partition for the OS and applications and set the mount point as / (the root).  Then create another partition for your /home/, and finally a swap partition.  This way, if an upgrade ever fails, you just erase the root partition, but you leave your home and swap partitions, which will be used immediately after a reinstall.

I found a guide that explains how to do this in more detail here:  [http://easierbuntu.blogspot.com/2008/03/setting-up-your-home-directory-on.html](http://easierbuntu.blogspot.com/2008/03/setting-up-your-home-directory-on.html)

I also wish upgrades were more bullet proof, or at least offered some kind of roll-back option afterwards in case it caused problems that you don't want to solve.  Though I'm the type of person who likes to stay on the cutting edge and upgrade to every release out there, instead of just the LTS releases (e.g., 7.04, 8.04, 9.04, etc).  Perhaps sticking with LTS makes a difference when it comes to upgrades; I wouldn't know.  Maybe someone else in here does...

If nothing else, just backup your /home/ folder because it's really all you'll care to want to recover in the end.  Everything else can be replaced with a fresh install of the OS and applications.

---

### Post by hyper_ch on 2009-03-22
I always do a fresh install - that's for me also the opportunity to get rif of things I don't want any longer. If you prepare yourself a bit a fresh install won't take much longer.

---

### Post by diablo75 on 2009-03-22
To be honest, I would say fresh installs take less time if you have partitioned things out as I mentioned above...

---

### Post by bumanie on 2009-03-22
I have a separate / and /home and thus only have to reinstall to /. I"ve found this to work very well. Canonical do give a warning prior to using the upgrade manager that the process could break your system, although the upgrade process often works well, it obviously is not perfect when accompanied by such a warning.

---

### Post by James_Lochhead on 2009-03-22
As long as you have a fast Internet connection, haven't installed lots of stuff from source and have a good idea of what packages you have installed it doesn't take long to do a fresh install.

Takes up under an hour these days.

Had a lot of practise though. Just come out of my distro hopping phase. Re-installing is really starting to bug me - installing 4 different distros in one day really takes it out of you!

---

### Post by mvalviar on 2009-03-22
Thanks for your insight. The thing that worries me is making a mistake. I made one before. I use xammp and stuff I needed to work on reside in /opt/lampp/htdocs. I backed up my home but forgot to make a copy of those. I ended up having to write those stuff from scratch. 

Having to do a fresh install takes the better part of the day. And the dangers of forgetting things scares me.

---

### Post by _Purple_ on 2009-03-22
Thats why its better to backup files regularly. :)

---

### Post by CatKiller on 2009-03-22
Some upgrades have gone more smoothly than others. I had a couple of problems with Edgy and a couple with Intrepid, but this install has been upgraded in place since Hoary. No major problems, just wrinkles to be ironed out. I generally upgrade on the day the new version is released, since I quite like ironing out wrinkles and filing bug reports to help correct any problems that have popped up. Most people don't like doing this, and so they **really** shouldn't upgrade straight away. Wait a couple of weeks for us less sensible people to have been hit by the bugs, and hopefully the bad things will have been fixed.

---

### Post by Sir Jasper on 2009-03-22
Hi,

I&#7743; using Simple Backup, without amending the presets, which include:

/var/
/home/
/usr/local/
/etc/

and the backup (which, in my case, runs in the background and takes about 5 minutes)is to a second non-Ubuntu internal drive. Also, I clone my Ubuntu main partition to an external usb drive every 10 days (which takes about 20 minutes) and I have successfully cloned back twice.

Where users do not take clones could they extend the use of Simple Backup (or another backup program)to include all their packages or even all the main Ubuntu partition?

My regards

Addendum:
On reflection, I&#7743; not at all sure what will happen with my first upgrade from 8.10 to 9.04. For instance I deleted all the games to save space - so will they be replaced automatically?

---

