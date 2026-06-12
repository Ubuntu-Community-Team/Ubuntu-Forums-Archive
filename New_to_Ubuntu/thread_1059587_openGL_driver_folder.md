---
title: "openGL driver folder"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by rcshah on 2009-02-03
Hi:
I'm new to Linux and installing a program which requires OpenGL.  I've made sure that my NVIDIA driver is up and includes OpenGL however I don't know how to respond when asked to indicate where OPENGL folders are...  Any ideas?

---

### Post by petervk on 2009-02-04
More information required.

Which program are you installing? Can you copy-paste the terminal contents here?

---

### Post by rcshah on 2009-02-04
I am installing Geant4 (particle interaction with matter program).  I did a find on files libGL* and found ones such as libGL.so.1 in /usr/lib.  However the Geant4 configuration file says that the OpenGL driver is not found in this directory.  What file might it be looking for?

If you want more info, please let me know what.  It doesn't seem that cutting and pasting the screen output would say more than I've explained but then again I'm too new to all this to really know...

I have also turned off the NVIDIA driver as this was creating annoying shifts in my readout on the monitor.  Thus I am just using the Ubuntu video driver.

---

### Post by petervk on 2009-02-04
This guy:
[http://hypernews.slac.stanford.edu/HyperNews/geant4/get/visualization/303.html](http://hypernews.slac.stanford.edu/HyperNews/geant4/get/visualization/303.html)
has some success by recompiling all of Geant4.

[https://wiki.bnl.gov/dayabay/index.php?title=Offline_Software_Installation_on_Ubuntu](https://wiki.bnl.gov/dayabay/index.php?title=Offline_Software_Installation_on_Ubuntu)

Do you have the "libglu1-mesa-dev" package installed?

---

### Post by rcshah on 2009-02-05
Under Package Manager I started checking off the all packages I could find on Mesa and OpenGL.  After doing this Geant identified the correct path on its own.

I will update this thread if I am stopped by additional problems in this vein.

Thanks for helping me by pointing out the files/names I needed to hunt around for.

---

