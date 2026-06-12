---
title: "VNC Viewer won't send caps"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by seattle vic on 2010-06-07
Has anybody seen this problem where the shift key does not work when using vncviewer?  I first use ssh to map a port:

ssh -L 2001:localhost:5900 remote_machine

then:

vncviewer localhost:2001

Hooks up fine, but I can't get anything sent over in caps.

---

### Post by seattle vic on 2010-06-07
One other thing I just noticed.  CapsLock key does work, but shift does not.

---

### Post by tehowe on 2010-08-09
this is kind of important in a case-dependent os.

note lack of capitalization. that's right; i'm on a remote connection, with no shift or caps lock. stop.

there is no alt-xxxx key for shift from what i can tell so it would be nice to know if there was a workaround for this. thanks. so far i've attempted vnc viewer and 'tight vnc viewer' and both send small caps only.

---

### Post by Peter09 on 2010-08-09
This is an outstanding bug - here is the report and workaround. (post 69)
 
[https://bugs.launchpad.net/baltix/+source/tightvnc/+bug/112955](https://bugs.launchpad.net/baltix/+source/tightvnc/+bug/112955)

---

### Post by tehowe on 2010-08-10
> **Peter09 said:**
> This is an outstanding bug - here is the report and workaround. (post 69)
 
[https://bugs.launchpad.net/baltix/+source/tightvnc/+bug/112955](https://bugs.launchpad.net/baltix/+source/tightvnc/+bug/112955)

+1

My remote shell is suddenly useful again.

The guy who braved x11vnc's documentation and found the workaround has a post about it...

[http://machine-cycle.blogspot.com/2009/02/vnc-shifty-keyboard-problems.html](http://machine-cycle.blogspot.com/2009/02/vnc-shifty-keyboard-problems.html)

[QUOTE=MachineCycle]At this point I had no choice but to guess a combination of command line  options that might fix my problem. Luckily, my first attempt payed off:
x11vnc [COLOR=green]-xkb[/COLOR] -ncache 0 --forever -localhost -display :0 -rfbauth .vnc/passwd &
I can happily join the other [monkeys]("http://en.wikipedia.org/wiki/Infinite_monkey_theorem") now.[/QUOTE]

---

