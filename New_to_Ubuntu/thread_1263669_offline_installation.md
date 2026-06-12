---
title: "offline installation"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by D BRUCE on 2009-09-11
hello 
I am new to ubuntu9.04 in fact new to linux
I got no internet connection.
Could anyone suggest how to download&install a media player,a C programming package and a Java programming package
thank you

---

### Post by dearingj on 2009-09-11
I'd recommend the following:
VLC media player: [http://packages.ubuntu.com/jaunty/vlc](http://packages.ubuntu.com/jaunty/vlc)
build-essential (for C/C++ programming): [http://packages.ubuntu.com/jaunty/build-essential](http://packages.ubuntu.com/jaunty/build-essential)
CodeBlocks (an IDE for C/C++ programming): [http://packages.ubuntu.com/jaunty/codeblocks](http://packages.ubuntu.com/jaunty/codeblocks)
Sun Java 6 JDK: [http://packages.ubuntu.com/jaunty/sun-java6-jdk](http://packages.ubuntu.com/jaunty/sun-java6-jdk)

You'll also need all the packages that are marked with a red ball on those pages.
You can download these packages from any computer that does have an internet connection, then save them to a portable disk such as a cd or usb, and put them on your non-Internet-connected computer.

---

### Post by t0p on 2009-09-11
Offline installation is a pain.  If you look up a package at [packages.ubuntu.com]("http://packages.ubuntu.org"), you'll see its dependencies listed.  But then you need the dependencies of dependencies... then the dependencies of dependencies of dependencies... then...  This is known as dependency hell, and is best avoided.  When I started with ubuntu I had no internet access.  Awful!  Then I worked out how to use my cellphone to get online and it was like being born again!

There's something called [AptOnCD]("http://aptoncd.sourceforge.net/") that might help too.  But then there's updates: a whole new problem...

---

### Post by Bartender on 2009-09-11
It would in all likelihood be less of a hassle to haul your PC to someplace with a broadband connection (even if it took all day) than to screw around with trying to install stuff offline.

---

### Post by mac9416 on 2009-09-11
> I got no internet connection.
Could anyone suggest how to download&install a media player,a C programming package and a Java programming package
thank you 

D BRUCE, use [Keryx]("http://keryxproject.org") to download the packages mentioned by dearingj. Keryx will get all the .debs for the packages and their dependencies. Then you can go to your offline machine and install them.

Good luck!

---

