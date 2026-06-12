---
title: "[SOLVED] I've crashed synapctic"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by jorge ortega on 2008-12-31
Please I need help. I tried to introduced a new repository in the repository list of Synaptic. This is what I typed: deb [http://mirror3.ubuntulinux.nl/hardyheron-seveas](http://mirror3.ubuntulinux.nl/hardyheron-seveas) freenx and now I can't access synaptic. A window pops up that says:
E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

---

### Post by jimmy the saint on 2008-12-31
in a terminal type 
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bkp
```
This will copy the repository sources list file to create a backup.
then type 
```
gksudo gedit /etc/apt/sources.list
```
The text editor will open up with root privilages so you can remove the offending line from the configuration file.

find the line that has the repository you added (47 probably) and add a hash mark # in front of the line so that it looks like   
#deb http.........blah blah

Save the file and try to open synaptic.

---

### Post by jorge ortega on 2008-12-31
Thanks very much Jimmy, that solved the problem. I should be more careful if i don't know shat i'm doing.
Thanks again

---

### Post by Ender41 on 2008-12-31
> **jorge ortega said:**
> Please I need help. I tried to introduced a new repository in the repository list of Synaptic. This is what I typed: deb [http://mirror3.ubuntulinux.nl/hardyheron-seveas](http://mirror3.ubuntulinux.nl/hardyheron-seveas) freenx and now I can't access synaptic. A window pops up that says:
E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


alt-ctrl-F1
login as yourself
sudo pico /etc/apt/sources.list enter
put in your password
put a # space in line 47 of that file
suspect it might be the mirror3 etc one :)


then hit F2 and choose to save

now sudo apt get update

This restores everything to original hopefully


Whoops ctrl-alt-F7 gets you back to thegui

---

