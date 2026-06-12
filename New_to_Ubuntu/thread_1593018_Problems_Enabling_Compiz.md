---
title: "Problems Enabling Compiz"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Tumpster on 2010-10-11
I just installed Merkat 10.10 and I'm trying to get visual effects running. Each time I go to custom or extra it thinks for a bit likes its going to apply them and tells me "Desktop effects could not be enabled." However I have the latest Nvidia drivers downloaded and installed off Nvidia's website. Any ideas how to get this working? I have a 512MB EVGA Nvidia 9800GTX+

---

### Post by rburkartjo on 2010-10-11
tump this seems to be a problem for a bunch of us here is i thread i started

[http://ubuntuforums.org/showthread.php?t=1592418](http://ubuntuforums.org/showthread.php?t=1592418)

and this thread started by day   [http://ubuntuforums.org/showthread.php?t=1592564](http://ubuntuforums.org/showthread.php?t=1592564)

---

### Post by Tumpster on 2010-10-13
Anybody? No one else is having this problem?

---

### Post by alkolkin on 2010-10-13
[SIZE=5][SIZE=4]I just installed 10.10 x64 **AND** 10.10 x86
I cannot use Normal** or** Extra Video effects in either one of these programs.
I have gone to all the websites that are reporting this problem and no one seems to have a fix that I as a newbie can understand or use.
The message is "Desktop effects could not be enabled"
I just did a straight install and updated from the RTM version.
I am running in a VMware virtual box on a Windows 7 x64 platform.  Lots of RAM, lots of speed, but this problem I cannot solve.
I have an Nvidia GeForce GTS 250 and this worked fine in the previous release of Ubuntu.  Restricted Drivers do not seem to be installed.
[/SIZE][/SIZE]

---

### Post by Tumpster on 2010-10-16
Agreed here, I find no fix, your telling me no one has figured this out?

---

### Post by Quackers on 2010-10-16
I don't know where you are, or even if it will help, but there was a new Nvidia driver available last night through a backport. It is version 260.19.12 and I got it from X Updates ([http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) maverick)

---

### Post by Tumpster on 2010-10-20
> **Quackers said:**
> I don't know where you are, or even if it will help, but there was a new Nvidia driver available last night through a backport. It is version 260.19.12 and I got it from X Updates ([http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) maverick)

I did this and it broke my graphics, I since reinstalled through command line with the latest package from Nvidia and have no issues with graphics but STILL have the problem with compiz/desktop effects.

After some digging, I followed these steps and everything works!:
I've followed this steps:

- backed up my compiz configurations (I've worked a lot on them ;) )
- Deleted compiz ppa
- purged all compiz packages
- cleaned apt cache
- updated packages list
- installed compiz again
- log out and log in
- I was getting the ugly blue compiz window decoration so just opened gconf-editor and set apps/gwd/use_metacity_theme to TRUE. 
- restored my settings

---

