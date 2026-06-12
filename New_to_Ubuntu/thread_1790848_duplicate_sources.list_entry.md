---
title: "duplicate sources.list entry?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by soylentcola on 2011-06-25
So I run the update manager every so often and this continues to pop up:

```
W: Duplicate sources.list entry http://extras.ubuntu.com/ubuntu/ maverick/main amd64 Packages (/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_maverick_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/libv4l/ppa/ubuntu/ maverick/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_libv4l_ppa_ubuntu_dists_maverick_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/earth/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-amd64_Packages)
```

I've checked in /etc/apt/sources.list but there's nothing in there that helps me to fix this problem...can someone direct me to where I should look to gte rid of these duplicates?

---

### Post by haqking on 2011-06-25
> **soylentcola said:**
> So I run the update manager every so often and this continues to pop up:

```
W: Duplicate sources.list entry http://extras.ubuntu.com/ubuntu/ maverick/main amd64 Packages (/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_maverick_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/libv4l/ppa/ubuntu/ maverick/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_libv4l_ppa_ubuntu_dists_maverick_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/earth/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-amd64_Packages)
```I've checked in /etc/apt/sources.list but there's nothing in there that helps me to fix this problem...can someone direct me to where I should look to gte rid of these duplicates?


use

gksudo gedit /etc/apt/sources.list

and commenting out the entries

then run

sudo apt-get update


then if all good you could try removing each comment at a time to see if they work again ?

---

### Post by nomko on 2011-06-25
Can you check this;

Open nautilus, go to the root folder and from there go to /etc/apt.
There are a a couple folders. Check the folder called preferences.d.
If you see under that folder files, check if 1 of those files contains the entry's you mentioned. There's a big change that you did something to your sources.list (to be found in the folder /etc/apt) in such a way that the entry's in the preferences.d are also to be found in sources.list. If you have the same lines in sources.list, then you can delete the files under preferences.d.

---

### Post by timur_ba on 2011-07-27
Is there a way to use a non-interactive script to find and delete duplicate entries in sources.list? 
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) is very good guide, but it doesn't mention that.

PS Please use search. The same asked at [http://ubuntuforums.org/showthread.php?t=1765754](http://ubuntuforums.org/showthread.php?t=1765754) and [http://ubuntuforums.org/showthread.php?t=1721784](http://ubuntuforums.org/showthread.php?t=1721784).

---

