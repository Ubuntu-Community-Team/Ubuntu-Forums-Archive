---
title: "unable to update"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by becca2010 on 2010-11-25
i hooked up my old system that im running ubuntu 8.04 on and i tryed to update to 8.10,not all of it upgraded now i cant open add/remove,synaptic package manager,or update manager

---

### Post by fly-by-night on 2010-11-25
Ubuntu 8.10 is not supported anymore.  I wonder why it's even offered as an upgrade?  You can upgrade from 8.04 to 10.04 directly - if you wish.

Look at the last post here:
[http://ubuntuforums.org/showthread.php?t=1295340](http://ubuntuforums.org/showthread.php?t=1295340)

Afterwards you might want to run this command to update your packages (with internet connection):
```
sudo apt-get update
```

If 10.04 was not available in Update Manager before, it should be now.

---

### Post by becca2010 on 2010-11-25
really,when i was going through all the forums it said i had to go through all the up grades one at a time to get to the latest,one site said to change my software sources (and i did) then upgrade to 8.10, did that but not all could be installed,also i tryed typing that in my terminal but it asks for my password but wont let me enter it

---

### Post by Enigmapond on 2010-11-25
Yes, you can upgrade between _LTS's_ but the best way still, and the way to avoid any problems is to just do a fresh install of Lucid off of a LiveCD.....

---

### Post by becca2010 on 2010-11-25
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'(message i get when i open update manager)                                                                          E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
(message from synaptic package manager)

---

### Post by Hippytaff on 2010-11-25
I would probably suggest backing everything up and doing a fresh install - but that's just what I would do because it's easier, and I'm a bit lazy :-)

---

### Post by Enigmapond on 2010-11-25
Like I said..._you are better off doing a fresh install_. You may try removing all your PPA info from the sources list and just use that standard ones for Ubuntu....I think it's trying to merge sources and it's unable.

---

### Post by becca2010 on 2010-11-25
yeah i guess i'll try and download the new version online,ty for the help

---

