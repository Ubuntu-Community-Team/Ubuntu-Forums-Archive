---
title: "Lucid-Are &quot;Backports&quot; the same as &quot;GetDeb&quot; for latest versions?"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by emarkay on 2010-06-10
Wiki says that "debian sid repository and the ubuntu backports repository" are as good for the "bleeding edge" updates as the seriously troubled and offline GetDeb repo.

I am looking to get the latest Avidemux  & BleachBit and have used GetDeb to easily install compiled versions.

Comments and are there even any Lucid Backports?

---

### Post by cozmicharlie on 2010-06-10
The version in synaptic can be determined by going to Synaptic, search for the package, right click and go to properties.  I have the backports checked and my version of Avidemux is 1:2.5.2-Oubuntu3.  the avidemux web site shows version 1.2.3.  I assume you are asking because the getdeb site is down.  You can install the latest versions (up to 2.6) by following the methods here:
[PHP]http://www.avidemux.org/admWiki/doku.php?id=build:compiling_avidemux[/PHP]

The Bleachbit version in Synaptic is 0.7.3.1.  The latest version shown on the web site is 0.8.  You can get a deb here:
[PHP]http://bleachbit.sourceforge.net/download/linux[/PHP]

Hope that helps

---

### Post by emarkay on 2010-06-11
> **cozmicharlie said:**
> The version in synaptic can be determined by going to Synaptic, search for the package, right click and go to properties.  I have the backports checked and my version of Avidemux is 1:2.5.2-Oubuntu3.  the avidemux web site shows version 1.2.3.  I assume you are asking because the getdeb site is down.  You can install the latest versions (up to 2.6) by following the methods here:
[PHP]http://www.avidemux.org/admWiki/doku.php?id=build:compiling_avidemux[/PHP]The Bleachbit version in Synaptic is 0.7.3.1.  The latest version shown on the web site is 0.8.  You can get a deb here:
[PHP]http://bleachbit.sourceforge.net/download/linux[/PHP]Hope that helps


Thanks for the specifics - I was relating more to the differences between Backports and "Get Deb" anmd how to "automagically" get the latest versions.

I am not an expert on compiling - maybe you can advise?  ;)  
I have been "bugged" with the Avidemux issue:
[http://avidemux.org/admForum/viewtopic.php?pid=43849#p43849](http://avidemux.org/admForum/viewtopic.php?pid=43849#p43849)
for a while now...

FWIW, Bleachbit is a complex and potentially invasive program; it is very dependent on configuration and I would prefer at least a tested version; between the Alpha/Beta and the official Ubuntu version - I figure that GetDeb allows a variety of versions from the former to the latter.

Thank you!

---

### Post by cozmicharlie on 2010-06-12
For Avidemux the link I provided has ubuntu specific instructions for compiling.  However, they need to be updated.  I did find 2.5 in the Karmic ppa. 
Regular version:
[HTML]https://launchpad.net/ubuntu/karmic/+package/avidemux-qt[/HTML]

x264 version:
[HTML]https://launchpad.net/ubuntu/karmic/+package/libx264-67[/HTML]

Bleachbt
The download for Ubuntu from the web site I provided is the stable version.  The latest stable version is 0.80.  To get it go to the web site:
[http://bleachbit.sourceforge.net/news/bleachbit-080-released](http://bleachbit.sourceforge.net/news/bleachbit-080-released)
Click on "Download">Linux
Find the ubuntu package and download it.

---

### Post by snowpine on 2010-06-12
Google is your friend: 

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)
[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

To answer your "what's in Lucid Backports?" question:

[http://packages.ubuntu.com/lucid-backports/](http://packages.ubuntu.com/lucid-backports/)

(not much, it would appear, or else technical difficulties with the site)

(edit) ps not a good idea to use Debian Sid repositories for Ubuntu; while they share similar legacy, they are not 100% compatible.

---

### Post by ankspo71 on 2010-06-12
Hi,
Here is a working mirror for getdeb and playdeb
[http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html](http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html)
But... if getdeb/playdeb is down, then the mirror probably can't offer updates, unless the original getdeb/playdeb goes back online.

---

### Post by alphacrucis2 on 2010-06-12
> **emarkay said:**
> Wiki says that "debian sid repository and the ubuntu backports repository" are as good for the "bleeding edge" updates as the seriously troubled and offline GetDeb repo.

I am looking to get the latest Avidemux  & BleachBit and have used GetDeb to easily install compiled versions.

Comments and are there even any Lucid Backports?

From my experience, ubuntu rarely if ever puts any stuff in backports. There is a launchpad ppa that has avidemux 2.5.3

[https://launchpad.net/~n-muench/+archive/programs-ppa]("https://launchpad.net/~n-muench/+archive/programs-ppa")

---

