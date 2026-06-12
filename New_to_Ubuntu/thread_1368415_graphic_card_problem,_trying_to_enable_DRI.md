---
title: "graphic card problem, trying to enable DRI"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by sugarnips on 2009-12-30
hi, im still very new to linux, on a quest to reinstall wow on my laptop (/sigh)...

im trying to verify if my dri is enabled with the *glxinfo | grep [COLOR=Red]rendering[/COLOR] command* and i get this:

X Error of failed request: Badrequest (invalid code or no such operation)
Major opcode of failed request: 135 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 16
Current serial number in umput stream: 16

any advice is greatly appreciated :)

edited for typo o.O

---

### Post by Mark Phelps on 2009-12-30
First off, you need to use the correct command.  It's "grep rendering" not "grep rending
".  

That doesn't solve your problem but at least you'll have the command right and see if direct rendering is enabled.

---

### Post by sugarnips on 2009-12-30
im sorry, i made the mistake rewritting it here, the error message is what i got from

glxinfo | grep rendering

---

### Post by sugarnips on 2009-12-30
edited my OP because of typo

---

### Post by sugarnips on 2009-12-30
shamefull bump :O

im scanning the web trying to find an answer, anyone have anything on this???

---

### Post by halitech on 2009-12-30
what video card? what version of Ubuntu? Have you installed any drivers for your video card?

---

### Post by sugarnips on 2009-12-30
> **halitech said:**
> what video card? what version of Ubuntu? Have you installed any drivers for your video card?

i have a raedon x1200 videocard, with ubuntu 9.10, i doubt i have installed any drivers, but where could i check for this?

---

### Post by halitech on 2009-12-30
ATI dropped support for the X series of cards at the same time Xorg made changes that have affected running Ubuntu with anything other then the installed Opensource drivers in versions after 9.04. I don't think you are going to get any 3d performance out the Opensource drivers. If you want a better experience, drop down to 8.04LTS and then you will be able to install either the ATI driver or the Ubuntu supplied driver which will give you 3d and better overall graphics.

---

### Post by clhsharky on 2009-12-30
HI sugarnips

   ATI still support legacy Xcards, in open source stack drivers.
Its easy to get 3D with the PPAs in Ubuntu from launchpad.

Go here for stable mesa,that gives you 3D.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

And here for updated drivers.
[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

Good luck and welcome to Ubuntu

Sharky

---

### Post by sugarnips on 2009-12-31
> **clhsharky said:**
> HI sugarnips

   ATI still support legacy Xcards, in open source stack drivers.
Its easy to get 3D with the PPAs in Ubuntu from launchpad.

Go here for stable mesa,that gives you 3D.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

And here for updated drivers.
[https://launchpad.net/~xorg-edgers/+archive/drivers-only]("https://launchpad.net/%7Exorg-edgers/+archive/drivers-only")

Good luck and welcome to Ubuntu

Sharky

i am curently downloading a ubuntu 8.04 bitorrent simply because i have no idea what to do with the 1st site you presented to me :S, i went into the details section and tried downloading whatever had raedon written within it, but i kept getting error messages...

what am i doing wrong, wont b installing ubuntu 8.04 untill at least 5 pm eastern time in case i can actually fix this.

---

