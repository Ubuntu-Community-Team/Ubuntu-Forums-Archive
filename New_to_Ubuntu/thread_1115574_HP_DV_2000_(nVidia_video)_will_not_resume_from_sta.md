---
title: "HP DV 2000 (nVidia video) will not resume from standby"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by sarc on 2009-04-04
This is a common problem but the story is a bit strange...

I intalled Intrepid with no tweaks and suspend/resume worked fine!

Then one day I clicked on "install Nvidia proprietary driver" on the hardware drivers menu.  Install failed, the driver was not installed, and the computer crashes on resume (no keyboard response).

Then I reformatted the root drive and reinstalled Intrepid from scratch... but this time resume still crashes!!!

Any ideas on a fix?  Thanks

---

### Post by linuxuser21 on 2009-04-04
It sounds like something is not compatible.

---

### Post by sarc on 2009-04-05
I fixed the suspend crash by manually installing nVidia river 180 from Synaptics instead of installing from the Administration-Hardware Drivers menu.  I got the idea from this web page:

[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

Cheerio

---

