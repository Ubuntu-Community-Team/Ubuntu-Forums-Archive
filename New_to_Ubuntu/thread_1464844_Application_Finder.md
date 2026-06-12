---
title: "Application Finder"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-04-28
Recently the "Application Finder" appeared in my accessories menu. It is nice but I can't find where it came from nothing turns up in file system search. I would like to add it to my other computers but nothing turns up in searches

---

### Post by tgm4883 on 2010-04-28
I don't see any Application Finder. Screenshot?

---

### Post by cmcanulty on 2010-04-28
Here it is it turned up today I guess when I did an update but I would love to install it on other machines.

---

### Post by ubunterooster on 2010-04-28
Is this the xcfe4-appfinder?
Turn on the terminal and type ```
xcfe4-appfinder
``` If this opens that is the same thing.

---

### Post by tgm4883 on 2010-04-28
Interesting, never seen that before. it's not on default ubuntu

---

### Post by ubunterooster on 2010-04-28
You might want to try ```
whereis appfinder
```
I doubt it is malware but...
BTW what version are you using?

---

### Post by cmcanulty on 2010-04-28
I guess not here is the output. Though that drives me nuts that a package has one name and a different name in the menus makes it very hard to find stuff sometimes.

```
cmcanulty@Gateway:~$ xcfe4-appfinder
No command 'xcfe4-appfinder' found, did you mean:
 Command 'xfce4-appfinder' from package 'xfce4-appfinder' (universe)
xcfe4-appfinder: command not found
cmcanulty@Gateway:~$ 
```

---

### Post by ubunterooster on 2010-04-28
I agree; different names are annoying. Try the code in Post #6.

---

### Post by cmcanulty on 2010-04-28
nothing comes up . I found this by a google search but it refers to a linux distrro I never even heard of, this is very strange! Scroll about 1/2 way down page I did the code and nothing came up

[http://bitethebyte.com/?tag=linux](http://bitethebyte.com/?tag=linux)

---

### Post by ubunterooster on 2010-04-28
Go to System>administration>synaptic package manager>settings>repositories>Other software. What links are there?

Suspect=malware???

Uh,have you edited the list or installed programs from online (other places than Ubuntu Software Center or Synaptic) ?

---

### Post by cmcanulty on 2010-04-28
I don't think it is malware, I like it.It won't let me paste the list but here is my sources page

# Salimane Adjao Moustapha's Ubuntu Karmic Koala 9.10 Sources list
#
# Repository List based on standard Karmic with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com KEY



# Ubuntu supported packages
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-proposed main restricted universe multiverse

#Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-backports partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-security partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-proposed partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-backports partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-updates partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-security partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-proposed partner

#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to lucid
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to lucid

#MPlayer Core Libraries
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
# deb [http://ppa.launchpad.net/rvm/libs/ubuntu](http://ppa.launchpad.net/rvm/libs/ubuntu) lucid main # disabled on upgrade to lucid

#vlc 1
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
# deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid main # disabled on upgrade to lucid

#GIMP (Testing Version)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 43BB102C405A15CB
# deb [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) lucid main # disabled on upgrade to lucid

# Ubuntu tweak
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220

#compiz-fusion
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
# deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) lucid main # disabled on upgrade to lucid

#skype

#firefox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
# deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#Ubuntu Mozilla Security Team
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A6DCF7707EBC211F
# deb [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free # disabled on upgrade to lucid

#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
# deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991

#empathy
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
# deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
# deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#emesene 1.5
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0CC1223EE2314809
# deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#gnome-globalmenu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
# deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main # disabled on upgrade to lucid

#gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
# deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#nautilus-dropbox
# deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) lucid main # disabled on upgrade to lucid

#gnome-colors theme
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
# deb [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) lucid main # disabled on upgrade to lucid

##Themes du ZgegBlog: Project Bisigi
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main # disabled on upgrade to lucid

# disper tool multiple graphical displays
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 66D5C734F6EFB904
# deb [http://ppa.launchpad.net/wvengen/ppa/ubuntu](http://ppa.launchpad.net/wvengen/ppa/ubuntu) karmic main
# deb-src [http://ppa.launchpad.net/wvengen/ppa/ubuntu](http://ppa.launchpad.net/wvengen/ppa/ubuntu) karmic main

# Virtualbox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free # disabled on upgrade to lucid

#Freenx Team (freenx, nxagent - remote X)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A8E3034D018A4CE
# deb [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) lucid main # disabled on upgrade to lucid

#Back In Time
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A423FD95416E75D
# deb [http://le-web.org/repository](http://le-web.org/repository) stable main # disabled on upgrade to lucid

#shutter
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
# deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) lucid main # disabled on upgrade to lucid

# ifuse for iphone/itouch
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9
# deb [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#Terminator
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
# deb [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#Drizzle
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FEC45DD06899068
# deb [http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu](http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu](http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#subversion 1.6
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
# deb [http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu](http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu](http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu) lucid main # disabled on upgrade to lucid



# deb [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) karmic main
# deb-src [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) karmic main

---

### Post by ubunterooster on 2010-04-28
Hmm all looks fine. (you have ubuntu-tweak; good!)Go to synaptic type in "application finder" Is any thing on the list shown as installed?

---

### Post by cmcanulty on 2010-04-28
Nothing comes up in Synaptic search. A real mystery

---

### Post by tgm4883 on 2010-04-28
I wonder if it is part of google desktop? [http://desktop.google.com/linux/](http://desktop.google.com/linux/)

Right click on it and put it on the panel, then right click on the panel icon and open up the preferences. That should show you the actual name that is launching it

---

### Post by antenna on 2010-04-29
> ```
cmcanulty@Gateway:~$ xcfe4-appfinder
No command 'xcfe4-appfinder' found, did you mean:
 Command 'xfce4-appfinder' from package 'xfce4-appfinder' (universe)
xcfe4-appfinder: command not found
cmcanulty@Gateway:~$ 
```

It's xfce4-appfinder like it tells you...  not xcfe. ;) 

And yes I believe it is that app.

---

### Post by cmcanulty on 2010-04-29
Sorry I did copy and paste but now I found it
```
cmcanulty@Gateway:~$ xfce4-appfinder
cmcanulty@Gateway:~$ whereis xfce4-appfinder
xfce4-appfinder: /usr/bin/xfce4-appfinder /usr/share/man/man1/xfce4-appfinder.1.gz
```

so now i will try and put it on other computers, thanks iy seems very useful especially when trying to set up a new system. I had searched in the software center but nothing came up for app finder I needed the xfce4 which indicates the software center ought to catch a search like that better

---

### Post by ubunterooster on 2010-04-29
Sorry, I frequently reverse the c and f

---

### Post by shagohad on 2010-05-19
I've installed it already but it doesn't see any programs installed. Anyone know how to fix?

---

