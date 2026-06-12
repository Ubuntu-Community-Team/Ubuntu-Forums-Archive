---
title: "Dream Aquarium in ubuntu 9.04"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by ichinpogs1 on 2009-07-06
Hi I am using ubuntu 9.04 .. my question is .. is it possible to run Dream Aquarium screen saver in ubuntu  9.04.[-o< i already experience running it using ubuntu 8.10 and its perfectly working. dream aquarium is amazing.. am just wondering if i can do that also in ubuntu 9.04..:?

---

### Post by cheyo on 2010-09-21
For those all who want Dream Aquarium as a screensaver in ubuntu 10.04:

first, open up a terminal and install wine using synaptic or apt-get.

Then, download and install dream-aquarium over wine, test it, it sould run pretty cool. I'm sure you'll know how to install windows apps under wine, if not, search for a tutorial ;)

Then, go to this dir and type this on your terminal:

```
cd /usr/lib/xscreensaver/ 
```

There, create a script for your screensaver:

```
sudo gedit aquarium 
```

And paste this code on to that file:

```
wine "C:\windows\command\start.exe" "C:\windows\Dream Aquarium.scr" 
```

SAVE the file and type this at your terminal

```
cd /usr/share/applications/screensavers 
```

once there, type this:

```
sudo cp fiberlamp.desktop aquarium.desktop 
```

then, change this section: 

```

TryExec=fiberlamp 
Exec=fiberlamp

```

to look like this:

```

TryExec=aquarium 
Exec=aquarium

```

Save and then install [[COLOR="Blue"]this screensaver[/COLOR]]("http://parker1.co.uk/apt/pool/main/e/eternity-screensaver/eternity-screensaver_0.4_i386.deb").

Done, check for aquarium at the screensaver preferences window (system/preferences/screensaver).


Notes:

* You'll not be able to see the screensaver in preview mode, just adjust it to appear at 1 min and wait.

* Sometimes you'll need to reboot for this to work, sometimes you don't. 

* Installing the extra screensaver is important because doing so will refresh the screensaver list at the screensaver selector on gnome, if someone knows how to do this in another way, then correct me, btw, eternity-screensaver is SO cool too ;)

Happy fishing.

---

