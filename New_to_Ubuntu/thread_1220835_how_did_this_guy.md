---
title: "how did this guy"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by enri2 on 2009-07-23
[http://seanbarman.deviantart.com/art/bespin-style-for-gnome-V2-129599031](http://seanbarman.deviantart.com/art/bespin-style-for-gnome-V2-129599031)
what program did have for the temperatures on the panel?

---

### Post by philinux on 2009-07-23
Looks like lm-sensors

---

### Post by enri2 on 2009-07-23
thanx. i couldn't find it 

do you know where I can get it?

---

### Post by desperado665 on 2009-07-23
Run the following in terminal:

```
sudo apt-get install lm-sensors
sudo sensors-detect 
```

hit Y to everything
then install sensors-applet

```
sudo apt-get install sensors-applet
```

sudo sensors if you just want to view the temps without the applets.

---

### Post by enri2 on 2009-07-23
thanx

what about cpu temp?:D

---

### Post by wizard10000 on 2009-07-23
> **enri2 said:**
> thanx

what about cpu temp?:D

If it's a fairly recent chipset you'll need a more current version of lm-sensors than what's in the repos.  What's in Jaunty repos is v1.3x and v3.x is current.  Here's a pretty good link -

[http://guide.ubuntuforums.org/showthread.php?t=1056681](http://guide.ubuntuforums.org/showthread.php?t=1056681)

---

