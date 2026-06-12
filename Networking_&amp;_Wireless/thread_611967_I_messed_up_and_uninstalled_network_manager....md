---
title: "I messed up and uninstalled network manager..."
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by Roadblock on 2007-11-13
If this post is in the wrong thread, I apologise. 

I just messed up and uninstalled Network Manager, now I can't get online. Is there a fix for this short of re-installing? I am using 7.10 Gutsy.

Any and all help appreciated. ;)

---

### Post by jetsam on 2007-11-13
Both of my Gutsy machines are networked without Network Manager.  It was causing problems, so I uninstalled it.  I think you only need it if you need wireless roaming to work.  

You should be able to go into System-->Administration-->Network and configure your network from there.  All I had to do was set the wired connection to use DHCP, and it's worked flawlessly since then.  

If you need roaming, I think people are installing WICD as an alternative to Network Manager.

If you just want to put Network Manager back, try:
```
apt-get install network-manager network-manager-gnome
```

---

### Post by Peter09 on 2007-11-13
Check that you have not got another network manager installed but not running, such as wifirader.

I did this a few weeks ago. You can get the individual packages from the web and download them to another machine, copy them onto a removable media and the reinstall them.

Go here to get your packages (any distribution)

[http://packages.ubuntu.com/gutsy/]("http://packages.ubuntu.com/gutsy/")

once on your machine they can be installed by just clicking on them. Network manager also removes some other packages that you may need, this will be highlighted by a dependency error. You just have to go and get that package as well. I think it needs 3 packages.

---

### Post by Roadblock on 2007-11-13
I have 2 computers on a wired router, with no networking set up. I am currently triple booting on this machine with Mepis, Sidux and Ubuntu. (Sorry, I should have stated that originally) I am currently online via Sidux.

@ jetsam - I already tried the "System-->Administration-->Network" avenue to no avail. I can't use apt-get, since I have no connection. I tried popping in my Gutsy Live CD and installing from there, but I couldn't get that to work. :(

@Peter09 - I will try grabbing the 2 files I need while I'm on now. (I think 2 was all that were deleted)

I knew there was a way, even if I had to re-install, keeping home intact, then using dkpg.list to install all the other files I had downloaded after isntallation. This should be a little easier and much quicker. I'll post back my results. 

THANKS GUYS!! =D>

---

### Post by Roadblock on 2007-11-13
That worked!!

I needed just 2 files:

network-manager
network-manager-gnome

Again, a thousand thanks. :)

---

