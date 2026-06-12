---
title: "How to use webcam ....?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by nikhilup on 2009-11-04
Which application should i use to take snapshots and to record video from webcam of my laptop....?

---

### Post by Wa1k3rTXRang3r on 2009-11-04
Try Cheese.

sudo apt-get install cheese

---

### Post by SunnyRabbiera on 2009-11-04
Cheese and wxcam
[http://www.getdeb.net/search.php?keywords=wxcam](http://www.getdeb.net/search.php?keywords=wxcam)

Both do a fair job, I prefer wxcam

---

### Post by nikhilup on 2009-11-04
Thanks a lot...!

---

### Post by nikhilup on 2009-11-04
But there is no package for Ubuntu 9.10 version for wxcam

---

### Post by SunnyRabbiera on 2009-11-04
> **nikhilup said:**
> But there is no package for Ubuntu 9.10 version

wxcam for jaunty should work in Karmic, same for cheese.
It should be fine

---

### Post by nikhilup on 2009-11-04
I am getting following error while installing wxcam


Selecting previously deselected package wxcam.
(Reading database ... 180317 files and directories currently installed.)
Unpacking wxcam (from wxcam.deb) ...
dpkg: dependency problems prevent configuration of wxcam:
 wxcam depends on libmjpegtools-1.9 (>= 1:1.9.0); however:
  Package libmjpegtools-1.9 is not installed.
 wxcam depends on libwxbase2.8-0 (>= 2.8.9.1); however:
  Package libwxbase2.8-0 is not installed.
 wxcam depends on libwxgtk2.8-0 (>= 2.8.9.1); however:
  Package libwxgtk2.8-0 is not installed.
dpkg: error processing wxcam (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 wxcam


what to do...?

---

### Post by SunnyRabbiera on 2009-11-04
is this from gdebi?
It should install the dependencies for you, if not we may have to install its dependencies manually.
Odd though as i was able to get wxcam working without issue on my karmic.
You using 64bit?

---

### Post by nikhilup on 2009-11-04
I tried installing this .deb file using terminal then i got this error.
I am using 32-bit.
How to install dependencies manually...?

---

### Post by SunnyRabbiera on 2009-11-04
> **nikhilup said:**
> I tried installing this .deb file using terminal then i got this error.
I am using 32-bit.
How to install dependencies manually...?

Well generally I suggest you dont install stuff with the terminal, gdebi should solve your issues.
Gdebi works  like the windows installer, double click your desired package  and it should install dependencies and all.
I would not worry about dependencies, unless you are determined to use the terminal.
Usually for new users i dont give out many terminal commands.

---

### Post by nikhilup on 2009-11-04
It worked with gdebi.
Thanks a lot...!

---

### Post by nikhilup on 2009-11-04
It worked with gdebi.
Thanks a lot.....!

---

### Post by SunnyRabbiera on 2009-11-04
> **nikhilup said:**
> It worked with gdebi.
Thanks a lot...!

No prob, I know a lot of people here give out commandline tutorials so i can understand some confusion.

---

### Post by avacado on 2009-11-05
instal the dependencies perhaps?
 
This might be done from the terminal or from system/admin/synaptic
 
or try 
sudo aptitude search libXX
sudo apt-get instal libXX
 
where XX is the full name of the dependency library your error message refers to.

---

### Post by nikhilup on 2009-11-06
It worked. Thanks..!

---

