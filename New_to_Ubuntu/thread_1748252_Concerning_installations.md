---
title: "Concerning installations"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by SapientShell on 2011-05-03
Under a short period I ran Ubuntu on my laptop. It was old and beaten however so it overheated due to a problem I couldn't find (running anything on this heap of junk is a strain on the system so I wasn't surpriced). I am, however, going to by a new laptop shortly and will be running a dual-boot of Ubuntu (probably 11.04) and Windows 7 (and a large storage partition for programs and media).

When I ran Ubuntu in the past I loved it but didn't really get to use it enough to learn all of the basics, and since I will be dual-booting I would like to learn the mechanics of installing programs on Ubuntu so that I'll know how to allocate the space on the partitions.

On Windows you simply dump the program you install pretty much anywhere you want, but how does that work with Ubuntu? Can you specify a path in the apt-get command or does the programs have to be installed on the OS partition?

If that's the case; How much space should I give the Ubuntu partition so that the OS can grow without restriction (for the avrage user)?

---

### Post by indytim on 2011-05-03
Make your life a whole lot easier as you start out by installing programs either from the package manager or the menu option (forgot what it's called).  These 2 approaches will do the "heavy lifting" for you with respect to dependencies, including in menu's and where to plunk the actual application and associated library(s).


I'm on a work Windows machine so I can't cite a specific example of what the software sources in called from the menu.

IndyTim / DataMan

---

### Post by SapientShell on 2011-05-03
So what you're saying is that I don't have to store Ubuntu programs on the OS partition?

Also, doing things the easy way is great but I really want to learn all the ways to work with the terminal as well since I have a little project lined up down the road where I'll probably only have a terminal to work with. So if there is a way to specify the path in the apt-get command I would still like to know. :)

---

### Post by el_koraco on 2011-05-03
Must be prefaced with sudo: 

apt-get install <package>
apt-get remove <package>
apt-get update (updates the list of repositories)
apt-get upgrade (upgrades the installed packages)

Need not be prefaced with sudo: 

apt-cache search <package> (shows the packages you can install)
apt-cache policy <package> (shows the packages you have installed that fit the search parameters)


The packages will be stored in the "system" partition of Ubuntu, yes.

---

### Post by AbsolutIggy on 2011-05-03
> **SapientShell said:**
> So what you're saying is that I don't have to store Ubuntu programs on the OS partition?

Also, doing things the easy way is great but I really want to learn all the ways to work with the terminal as well since I have a little project lined up down the road where I'll probably only have a terminal to work with. So if there is a way to specify the path in the apt-get command I would still like to know. :)

No, you probably will. When installing, the best thing to do is probably make on partition for / (the OS) and one for /home.
APT will install programs usually in places like /usr.

If you give your ubuntu partition something like 20GB you should be fine. I have quite a few programs installed and am at 7GB now (excluding home).

---

### Post by K_45 on 2011-05-03
Apt will install programs typically in /usr/bin or /opt if they are large. You would normally install them on the same partition.

---

