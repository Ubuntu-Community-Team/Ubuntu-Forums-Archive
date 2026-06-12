---
title: "GoogleEarth"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by jakespet on 2009-04-06
Okay! Here's my problem. I just installed GoogleEarth5 in Ubuntu 8.04. I get the message that it was succesfully installed, but when I run it this is the message I get: " could not create directory /root/Googlee Earth .when I hit return I get the following message:
could not write to the current cache or myplaces file location. The values will be set as follows:
My Places Path: "/home/bob/.googleearth"
Cache Path: 
"/home/bob/.googleearth/Cache"

It will open up and as soon as the tips screen opens, Google Earth will close.

So, can anyone help me with uninstalling it or help get it running?
Thanks for your help

---

### Post by ronocdh on 2009-04-06
It sounds like you somehow installed it to a non-default location. I would try a **sudo aptitude purge googleearth**(replace "googleearth" with whatever the actual name of the package is!) to completely remove it, then reinstall.

It shouldn't need to install anything to /root.

---

