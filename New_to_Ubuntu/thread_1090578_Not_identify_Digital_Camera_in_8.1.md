---
title: "Not identify Digital Camera in 8.1"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by nishanthaMe on 2009-03-08
I have a panasonic digital camera and it was identified and allow to access its content in ubuntu 8.04 but I installed ubuntu 8.1 in my computer and now it do not detect the camera and says error mounting the device. Is there anyway to do this ?

cheers

Nishantha

---

### Post by kansasnoob on 2009-03-08
Go to synaptic and see if "gtkam" is installed. Not absolutely sure if that will help or not.

You may also want "gtkam-gimp" if that does help with mounting.

It's also remotely possible that installing the package "pmount" from synaptic could help.

---

### Post by nishanthaMe on 2009-03-10
I installed all those things but again the same error.I don't understand to work it in 8.04 but not to work in 8.1

---

### Post by halovivek on 2009-03-10
try to install picasa for linux. i hope it will help you.
can you  see the mounted camera folder in the linux?

---

### Post by nishanthaMe on 2009-03-15
No. no mounted folder for the camera. error is for mounting I guess.

---

### Post by rustutzman on 2009-03-15
If you see the camera folder at all run nautilus as root and try to open the folder then. ```
gksudo nautilus
```

---

