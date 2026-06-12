---
title: "Sound problems"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by knipp21 on 2009-04-28
ok so im running ubuntu 8.10 on my hp tx2000 and my headphone jack doesnt work...its as if it doesnt exist when headphones are plugged in...also is there any way to make the touchscreen work...im new to this

---

### Post by Favux on 2009-04-28
Hi knipp21,

Welcome!

These links are about Hardy (when the TX2000 came out) but most applies to Intrepid.  I think most of us started out with mirosol's HOW TO:  [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)  And some other useful setup threads are:  [http://ubuntuforums.org/showthread.php?t=837657&highlight=tx2000](http://ubuntuforums.org/showthread.php?t=837657&highlight=tx2000) and [http://georgia.ubuntuforums.org/showthread.php?t=792669](http://georgia.ubuntuforums.org/showthread.php?t=792669)

To setup Wacom you have to install the drivers and edit your xorg.conf.  Once things are working you calibrate your tablet with wacomcpl and then install a rotation script so you can rotate your screen into tablet mode.

Let's start with the drivers.  The linuxwacom drivers that come with Intrepid are version 0.8.1-4 (search wacom in Synaptic Package Manager).  We should update you to at least 0.8.1-6.  So go to Loic2's Wacom wiki:  [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7166546](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7166546)  Near the top you'll see the Ubuntu 8.10 section.  Under that will be "1. Download the updated packages :".  You are going to download the two amd64 deb.s (Debian packages) onto your desktop.  Double click on them and they will automatically be installed.  Note it is important to make sure that the wacom-tools and wacom drivers (the xserver-xorg-input-wacom package) are always the same version.

Then we can move on to configuring your xorg.conf.

Hope this helps.

Edit:  Just to be sure you're talking about a TX that came out a year or more ago, right?  Not one that just came out and is also called a touchsmart (multi-touch)?

---

