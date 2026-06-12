---
title: "Trouble installing WINEASIO"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by geoff_sct on 2011-06-17
I've been trying to figure out how to install this dll but the instructions that come with it are for someone much more advanced.  Here's what it says to do :


Before installation edit the prefix path in the Makefile
PREFIX = <root path you use>

usually this will either be

PREFIX = /usr
or
PREFIX = /usr/local

Copy the file asio.h from Steinberg's asio-sdk to the wineasio directory

then execute: make
and as root:  make install

then, again as normal user: regsvr32 wineasio.dll



As normal huh? Ok I'm sure this all makes perfect sense to you guys. Maybe I'm just not cut out for this.

---

### Post by jtarin on 2011-06-18
Got link to these instructions? What version of Ubuntu are you using?

---

### Post by jtarin on 2011-06-18
I found[ these]("http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio") instructions for Reaper (thinking maybe that's your goal)but can't guarantee they will work on your version.....quite possible though as it's gonna be a Wine install. Pretty straight forward.

---

### Post by geoff_sct on 2011-06-18
jtarin, Thanks for the reply. I copy/pasted those installation instructions directly from the "Read Me" file in the downloaded Wineasio.  Thanks for the link. Maybe I'm making this more difficult than it is.

---

