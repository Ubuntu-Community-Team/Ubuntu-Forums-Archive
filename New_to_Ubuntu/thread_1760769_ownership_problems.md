---
title: "ownership problems"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by abraxas334 on 2011-05-17
My motherboard broke recently and I had to get a new computer. Rather than reusing my old hard-drive I did a fresh install on a new harddrive. I have an external harddrive docking station with a usb connector, so I thought that way I'll be able to have access to my old harddrive. However I only have read permission on the Linux drive and some directories are completely inaccessible.
The permissions are: 
Owner: 1001-user #1001
and group: 1001
the linux distributions should be the same and my username has not changed.
How can I get access to my files again?
Thank

---

### Post by compmodder26 on 2011-05-17
My guess is the the numeric id number of your user account is different than that of your previous install.

Simple fix is to open a terminal and do this:

```
cd <directory where your old hard drive is mounted>
sudo chown <your username>:<your main group> -R *
```

This will give you ownership of everything on that drive.

Note: I assume you only want to do this to get files off of the old drive?  If you plan to run Ubuntu on the old drive at a later point then changing ownership off root could do some funky stuff.

---

### Post by abraxas334 on 2011-05-17
Thank you! It worked :)

---

