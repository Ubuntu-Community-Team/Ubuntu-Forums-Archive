---
title: "[SOLVED] ./configure doesn't find packages needed"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by -exec- on 2008-12-31
I'm trying to build awn (avant-window-navigator) from source. Everything I've did is exactly as in this [[how-to]("http://wiki.awn-project.org/InstallingFromSource")]. If I try running autogen.sh, I get errors

```
checking for PYGTK... configure: error: Package requirements
(gtk+-2.0 pygtk-2.0 >= 2.10.0) were not met:

No package 'gtk+-2.0' found
No package 'pygtk-2.0' found
```
 
Surprisingly I have all packages needed installed - for pygtk-2.0
```
python-gtk2
python-glade2
python-gtk2-dev
```
as well as for gtk+-2.0
```
libgtk2.0-0
libgtk2.0-dev
```

apt-get says they all are at newest versions (> 2.10.0).

Has anyone encountered similar problems?

---

### Post by gn2 on 2008-12-31
Why build from source when it's available in the repositories along with awn-manager?

---

### Post by gjoellee on 2008-12-31
have you tried installing from repo?
```
sudo apt-get install avant-window-navigator
```

---

### Post by -exec- on 2008-12-31
I have all released awn stuff installed and running. I'm trying to install from source because development version has a lot of new features (and, of course, lack of stability).

However, why I'm using hard way is not very important, because error comes not from awn itself, but from ./configure script and <maybe> from pkg-config (I've tried to reinstall it too).

---

### Post by kaivalagi on 2008-12-31
You could try the version of awn available from this ppa:

```
## +++ Reacocard's Ubuntu Repository +++
# wget http://download.tuxfamily.org/syzygy42/F4ECF181.gpg -O- | sudo apt-key add -
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main

```

Just uninstall all apt based packages before updating, then use the *-bzr package names...

Works for intrepid and hardy

More info here: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by -exec- on 2008-12-31
Thanks! That solved my problem. But I still don't understand where do the errors come from? Bad configure script? Unset environmental variables (I haven't done any customizations)? pkg-config?

---

### Post by albinootje on 2008-12-31
> **-exec- said:**
> Thanks! That solved my problem. But I still don't understand where do the errors come from? Bad configure script? Unset environmental variables (I haven't done any customizations)? pkg-config?

You can see for yourself. There's normally a logfile of the configure script, I forgot the name, an :
```

ls -latr

```
in the directory where you did ./configure would probably show it as one of the last entries.

---

