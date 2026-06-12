---
title: "What is the difference between apt-get and aptitude?"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by redfox1160 on 2010-10-27
I have come across commands that use both apt-get or aptitude. I think I have read that aptitude is an older version (I could be wrong), but could someone inform me of the difference between them and when I should use one over the other? Thanks!

---

### Post by irv on 2010-10-27
your answer can be found at: [http://www.linuxquestions.org/questions/debian-26/apt-get-vs-aptitude-363365/]("http://www.linuxquestions.org/questions/debian-26/apt-get-vs-aptitude-363365/")
For simple question like this you can do a google search and find the answer very quickly.

---

### Post by NertSkull on 2010-10-27
[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by lavinog on 2010-10-27
aptitude is no longer installed by default in maverick

It had a curses interface (like a menu based interface)
It had minesweeper built in to it.

The search results between aptitude search and apt-cache search are almost always different.  I think apt-cache searches the description while aptitude searches the package name:
```

$ aptitude search chrome
i   xserver-xorg-video-openchrome  - X.Org X server -- VIA display driver    


$ apt-cache search chrome
libslang2-dev - The S-Lang programming library, development version
libxpm-dev - X11 pixmap library (development headers)
libxpm4 - X11 pixmap library
libxpm4-dbg - X11 pixmap library (debug package)
splix - Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
xserver-xorg-video-openchrome - X.Org X server -- VIA display driver
dicomscope - The OFFIS DICOM Viewer
libjs-excanvas - HTML5 Canvas for Internet Explorer
libv8-2.0.3 - V8 JavaScript Engine
libv8-dbg - Development symbols for the V8 JavaScript Engine
libv8-dev - Development files for the V8 JavaScript Engine
linuxlogo - Color ANSI System Logo
minidjvu - Monochrome DjVu multipage encoder, single page encoder/decoder
murrine-themes - themes for gtk2 murrine engine
prboom - clone of the legendary first person shooter Doom
xpat2 - Generic patience game for X11
xserver-xorg-video-via - X.Org X server -- VIA display driver (dummy transitional package)
yabasic - Yet Another BASIC interpreter
picon-domains - Picon (Personal Images) database of for Internet domain logos.
picon-misc - Picon (Personal Images) database of common accounts and misc.
picon-news - Picon (Personal Images) db of Usenet newsgroups and hierarchies
picon-unknown - Picon (Personal Images) database for very high-level domains
picon-usenix - Picon (Personal Images) db of Usenix conference attendees
picon-users - Picon (Personal Images) database of individual Internet accounts
picon-weather - Picon (Personal Images) database for displaying weather forecasts.
chromium-browser - Chromium browser

```

---

### Post by ArgusVision on 2010-10-27
Hmm... never really had reason to give that question much thought. Thanks for the links irv and NertSkull. Very informative. I can check the box that I learned something new today. :)

---

