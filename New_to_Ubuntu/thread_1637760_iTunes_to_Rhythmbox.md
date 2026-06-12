---
title: "iTunes to Rhythmbox?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by rebornjumpman on 2010-12-04
I recently converted to Ubuntu from Vista and I'm wondering if there is a (relatively) quick way to convert my iTunes library to be compatible with Rhythmbox.

---

### Post by dondiego2 on 2010-12-04
I'm not sure what you are talking about.  You can just select the folder your music is in from Rhythmbox and it should find it all.  Just go to edit/preferences and set your library location.  You can set more than one.

---

### Post by uRock on 2010-12-04
If you have not yet installed codec to be able to play MP3 and such, then open your menu and go to Ubuntu Software Center and in the search field enter ubuntu-restricted-extras, then once you find it click to install it. This will let you play iTunes files, such as MP4s.

If you want to install via the command line, then go in the menus to Applications> Accessories> Terminal, then copy and paste this command;```
sudo apt-get install ubuntu-restricted-extras
```

Explanation of this command

**sudo**= super user do, which gives the terminal root permission to install/configure software

**apt-get**= is the application the manages retrieving and installing softwares

**install**= is an argument telling apt-get what to do with the package that it is retrieving

**ubuntu-restricted-extras**= is the software to be installed.

---

