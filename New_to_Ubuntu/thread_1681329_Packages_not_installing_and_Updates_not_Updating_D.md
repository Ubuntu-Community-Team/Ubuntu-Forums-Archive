---
title: "Packages not installing and Updates not Updating D:"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by bbundy09 on 2011-02-04
Hey guys,

I've been using Ubuntu for over a month now, and just recently I've been having issues with installing the updates and packages in Ubuntu AMD64.....I got an update and tried to install, and I keep getting this:
```
E: libuuid1: subprocess installed post-installation script returned error exit status 9
```

For some reason, libuuid1 is malfunctioning and hindering progress.....

When I try to install packages (for this example pydance from the Terminal), I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  pydance-music
Suggested packages:
  ddrmat-source mp32ogg python-psyco
The following NEW packages will be installed:
  pydance pydance-music
0 upgraded, 2 newly installed, 0 to remove and 43 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

```

Halp?

---

### Post by lisati on 2011-02-04
The error message you got usually happens when you've got something else open that can update your system. Close Synaptic and the software center before running update manager.

---

### Post by Dutch70 on 2011-02-04
If you can't find what else is running, synaptic, software center, etc... You can try rebooting.

---

### Post by bbundy09 on 2011-02-04
I closed the Software Center, and had no programs open that updates, I thought....and got the same error....

and I've restarted a few times before.  This has been happening to me the last couple of days, and I just now got to dealing with it.

---

### Post by Dutch70 on 2011-02-04
Wow, it's beyond my knowledge then. My only other idea is to open system monitor > processes & see if you can find something else running there, that shouldn't be. If so, you may be able to reinstall it to fix the issue.

---

