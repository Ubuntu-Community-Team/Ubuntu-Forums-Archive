---
title: "VNC from Mac to Ubuntu, actions can't be seen on Mac"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by SlappyPappy on 2010-05-15
I can get the screen to come up on my Mac of the Ubuntu desktop but when I click on something to get an action in Ubuntu the Mac doesn't show what is happening, it's as if it's frozen.

Windows can be opening and closing on Ubuntu but you don't see them taking place on the Mac.

Any ideas as to how you can VNC into Ubuntu and get it to work right? 

Thanks.

---

### Post by XCan on 2010-05-15
Unfortunately, if you run a properiatary driver in Ubuntu, VNC is broken by default. The easiest workaround, currently, is to disable desktop effects in Ubuntu.

[https://bugs.launchpad.net/xorg-server/+bug/353126](https://bugs.launchpad.net/xorg-server/+bug/353126)

---

### Post by Excedio on 2010-05-15
> **XCan said:**
> Unfortunately, if you run a properiatary driver in Ubuntu, VNC is broken by default. The easiest workaround, currently, is to disable desktop effects in Ubuntu.
 
[https://bugs.launchpad.net/xorg-server/+bug/353126](https://bugs.launchpad.net/xorg-server/+bug/353126)
 
 
I wouldn't call this the easiest work around.
 
 
However, I would call this the easiest work around: [http://opensourceexcedio.wordpress.com/2009/12/15/band-aid/](http://opensourceexcedio.wordpress.com/2009/12/15/band-aid/)
 
[COLOR=darkred]Disclaimer:[/COLOR] Doing this will slow down the connection as it refreshes the entire screen instead of just the pieces that have changed.

---

### Post by SlappyPappy on 2010-05-15
Thanks for the help you guys. Speed isn't a big issue for me, just being able to access the Ubuntu machine is though. I'm going to set up several Ubuntu boxes that will be on a local network that I can get to from a Mac.

Good stuff.

---

