---
title: "Mouse Control using Microsoft Kinect"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by offchr8 on 2011-04-27
Hi everyone,
I'm a sophomore in college researching mouse control using an Xbox Kinect, I was told that XWrapper.config would be the place to find the name of the function that controls the X, Y position of the mouse. I then would want to replace that code with the Kinect Sensor position of the active pointer from a sample. I dont know how to access this file through the terminal to see its code. If anyone knows the name of the functions or knows how to modify it would be a great help.

Thanks

---

### Post by kat_ams on 2011-07-23
had you already discovered the openkinect website and the Kinect Mouse project

OpenKinect
[http://openkinect.org/wiki/Main_Page](http://openkinect.org/wiki/Main_Page)

Kinect-Mouse project
[https://github.com/Ooblik/Kinect-Mouse/](https://github.com/Ooblik/Kinect-Mouse/)

I'm trying to compile Kinect-Mouse on Lucid as of writing this.

---

### Post by Sef on 2011-07-23
Moved to ABT.

---

### Post by chaos0422 on 2011-12-21
Im just trying to get the kinect mouse to work and im having issues installing libglut3 on 11.10. I found a work around but im not sure about on of the steps if someone could help me. the red part is what i dont get...

[LIST]
[*]Install freeglut3-dev, which replaced libglut3-dev in oneiric:
 [INDENT] sudo apt-get install freeglut3-dev
 [/INDENT]
[*]Install equivs, which will allow you to create pseudo-packages:
 [INDENT] sudo apt-get install equivs
 [/INDENT]
[*][COLOR=Red]Create a file *libglut3-dev.conf* for the pseudo package linking libglut3-dev and freeglut3-dev:[/COLOR]
 [INDENT] Section: misc
 Priority: optional
 Standards-Version: 3.6.2
 Package: libglut3-dev
 Depends: freeglut3-dev
 Description: temporary package to satisfy dependencies of Ubuntu 11.04 packages on 11.10
 [/INDENT]
[*]Convert it to an actual package and install it:
 [INDENT] equivs-build libglut3-dev.conf
 sudo dpkg -i libglut3-dev_1.0_all.deb
 [/INDENT]
[/LIST]

---

