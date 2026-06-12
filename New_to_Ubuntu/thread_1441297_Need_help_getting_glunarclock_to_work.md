---
title: "Need help getting glunarclock to work"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by boxcorner on 2010-03-28
I used Synaptic to install glunarclock version 1:0.32.4-11ubuntu2, but couldn't get it to work.  When I tried to add the applet to the panel, it displayed "Lunar clock has quit unexpectedly".  When I clicked on reload, it displayed "The panel encountered a problem while loading OAFIID:GNOME_GLunarclockApplet".  I understand this package isn't supported by Canonical.

Then I discovered that version 0.34.1 was released on 17 March 2010, so I   downloaded it from [http://sourceforge.net/projects/glunarclock/files/]("http://sourceforge.net/projects/glunarclock/files/")

However, I don't understand the part in the installation instructions [http://glunarclock.sourceforge.net/installing.php]("http://glunarclock.sourceforge.net/installing.php") where it talks about giving the appropriate options to the configure script (see ***** below).  The instructions say, extract the tarball, enter the glunarclock directory and execute: 

$ ./configure --prefix=... (***** see comment below)
$ make
$ su
# make install

***** Give the appropriate options to the configure script. For example:

$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --libexecdir=/usr/lib/gnome-panel

Could someone please help me understand how to configure this script for my Ubuntu installation?  Thanks.

_Updated: Monday 11 October 2010_

Used Synaptic Package Manager to do the following:
[LIST]
[*]Complete Removal
[*]Reinstallation
[/LIST]
Added the applet to the Panel:
[LIST]
[*]moved the mouse pointer to the Panel
[*]right-clicked on the Panel
[*]selected Add to Panel
[*]selected Lunar Clock
[/LIST]
Installed version 0.34.1

Use [http://www.http://wikimapia.org/]("http://www.wikimapia.org/") to establish latitude and longitude.

Right-click on the Lunar Clock icon > Preferences > Location

Further info available here: [http://glunarclock.sourceforge.net/]("http://glunarclock.sourceforge.net/")

---

