---
title: "Problem with VLC"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by russ.tyler on 2009-02-28
I'm having trouble getting VLC to install, I've tried opening up the software sources files and checking everything in the left had column and in the ubuntu tab but its still giving me an error when I open the synaptic package manager thats the error I keep getting can't figure out whats wrong

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by adult swim on 2009-02-28
run these commands one at a time
```
sudo dpkg --configure -a

sudo apt-get update

sudo apt-get install vlc
```

---

### Post by hyperyoda on 2009-02-28
> **russ.tyler said:**
> I'm having trouble getting VLC to install, I've tried opening up the software sources files and checking everything in the left had column and in the ubuntu tab but its still giving me an error when I open the synaptic package manager thats the error I keep getting can't figure out whats wrong

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

You may have a corrupted package cache (the package may not have downloaded completely or could have been altered in some way).

Look in /var/cache/apt/archives/ and /var/cache/apt/archives/partial
If it is in partial it is not completely downloaded. If it is in /var/cache/apt/archives/ verify the package is complete by doing:
$ md5sum /var/cache/apt/archives/package.deb
And comparing it to a value from a trusted repo.

To get it working I'd try:

$ dpkg --configure -a

If that fails do:

$ apt-get update

Then do:

$ dpkg --configure -a

check the install status flags by doing:

$ dpkg -l | grep package

If it is only partially installed try:

$ apt-get -f install

Zach

---

### Post by russ.tyler on 2009-03-01
Thanks guys I tried that stuff but whenever I'm runnin something in my terminal it either just shuts down on me or it tells me its not the right password so i'm just gonna mess with it and see what happens

---

