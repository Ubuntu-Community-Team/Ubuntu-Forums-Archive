---
title: "Upgrade"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by bigal1932flying on 2009-04-21
Tried to upgrade 8.10 using alternate iso and received the following message:
An unresolvable problem occurred while calculating the upgrade:
The package 'xubuntu-desktop' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
Is there any way to fix this?

---

### Post by cariboo on 2009-04-22
Before doing any upgrades, I'm assuming you are trying to upgrade to Juanty, make sure you have all ppa's and other repositories disabled in /etc/apt/menu.list, and make sure your current version is fully up to date.

---

### Post by peakshysteria on 2009-04-22
Then do:

> Upgrading from Ubuntu 8.10

To upgrade from Ubuntu 8.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.04' is available. Click Upgrade and follow the on-screen instructions. 

From;[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by cariboo on 2009-04-22
To disable ppa's and none Ubuntu repositories open /etc/apt/sources.list in a text editor as root.
Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

then look for any lines similar to this:

```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

```

put a **#** to the left of **deb** to comment out the entery. Any other lines that don't have Ubuntu in them should be commented out too.

---

### Post by bigal1932flying on 2009-04-23
Could not find items mentioned so did some web searching and after some aborted attempts managed to remove xubuntu desktop.
I was then able to install 9.04 from the iso file I had downloaded.
Thanks for the help.

---

