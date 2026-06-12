---
title: "What does this mean?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libdvdnav4 (>= 0.1.10) but it is not installable
           Depends: libenca0 (>= 1.9) but it is not installable
           Depends: libfaac0 (>= 1.26) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: libjack0 (>= 0.109.2) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libsvga1 but it is not installable
           Depends: libx264-57 (>= 1:0.svn20071224) but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages
root@ericeclifford:/# 



thats after I type in apt-get install mplayer. for my live cd customization(edit folder)

---

### Post by 5BallJuggler on 2009-02-04
Are you running from the Live CD? If so you need to install Ubuntu for it to allow packages to be added to your system.

---

### Post by jerome1232 on 2009-02-04
> **5BallJuggler said:**
> Are you running from the Live CD? If so you need to install Ubuntu for it to allow packages to be added to your system.

Actually you can install packages on a live cd (how else can you get encryption and lvm working from a desktop cd ;) ), I've installed programs from a live cd all the time. More than likely universe or multiverse needs to be enabled?

---

### Post by ericeclifford on 2009-02-04
Im running from a external harddrive that I installed from a live cd. But I am not running from a live cd. I a installed it from one and I installed media player to the harddrive but it dont let me for my custom live cd I am trying to make.

---

### Post by Flimm on 2009-02-04
How you tried refreshing the list of available packages?
```
sudo apt-get update
```

---

### Post by ericeclifford on 2009-02-04
Yes I tried that many times. Didnt work at all :(

---

### Post by dox_drum on 2009-02-04
Perhaps you do not have installed the repository pages where those updates are.

---

### Post by bwang on 2009-02-05
Post the contents of /etc/apt/sources.list

---

