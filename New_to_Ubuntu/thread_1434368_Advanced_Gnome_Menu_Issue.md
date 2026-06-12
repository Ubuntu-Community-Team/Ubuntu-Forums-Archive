---
title: "Advanced Gnome Menu Issue"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by amnite on 2010-03-20
Im not shure if this is the best place to post but i really didnt find a fitting category. But anywho... Im using wubi\Ubuntu\Karmic and i just downloaded Advanced Gnome Menu. My only issue is how to i get anything to show up. When i click to pull up my menu I get the welcome text, execute, search and favorites, but nothing under the menu area.. Ive right clcicked and went to edit gnome menu and have the items i want checked but still no menu... any help?

---

### Post by ankspo71 on 2010-03-22
Hi,
After reading your post I decided to try it out. I was having the same  problem as you're describing. I tried version 0.8.3-2 (deb). 

Have you tried compiling it from a source file? (I haven't yet, but sometimes this helps work out quirks)

**Source install:**
 
[LIST]
[*]Download the source
[*]Untar it on your pc
[*]give the command ./install.sh
[/LIST]

**Svn install**
 
[LIST]
[*]Install subversion (on debian-ubuntu: sudo apt-get install  subversion)
[*]Create a directory where put the program.
[*]Open a terminal and move to that directory
[*]Run this command: svn checkout [http://advancedgnomemenu.googlecode.com/svn/trunk/](http://advancedgnomemenu.googlecode.com/svn/trunk/)  advancedgnomemenu-read-only
[*]Enter into the new folder and execute ./install.sh
[*]This script will install the latest svn version of agm (please, note  that if you use the agm-panel you must remove it and re-add if you want  to see changes, if you reboot you obtain the same..).
[/LIST]
above info borrowed from [http://www.sciallo.net/AGM/](http://www.sciallo.net/AGM/)  (AGM homepage)
hope this helps.

---

### Post by readycarpenter on 2010-03-22
I would not install much using wubi, I have have many problems in (wubi), it is mainly for testing ubuntu when you are not committed, take the full plunge and partition your drive and install ubuntu on an dedicated partition. you will find it will run 10x faster than wubi

---

### Post by ankspo71 on 2010-03-22
Hi,
I tried compiling from source and svn with no change. I don't know what the problem could be.

Have you tried gnomenu? (It's a favorite with alot of people and it supports themes)
[https://launchpad.net/gnomenu/](https://launchpad.net/gnomenu/)
PPA that has deb packages for gnomenu is here: (easier installation)
[https://launchpad.net/~gnomenu-team/+archive/ppa]("https://launchpad.net/%7Egnomenu-team/+archive/ppa")
_[Direct link to version 2.3.0.]("https://launchpad.net/%7Egnomenu-team/+archive/ppa/+files/gnomenu_2.3.0-0%7Eppa1_all.deb")_ (deb package)

gnome-main-menu is found in Synaptic Package Manager.
It's almost like the menu in Linux Mint.

gimmie is an alternative type of menu.
[http://beatniksoftware.com/gimmie/Main_Page](http://beatniksoftware.com/gimmie/Main_Page)
(this might be in your version of ubuntu too)

I just thought I would mention these since AGM is not working.

---

