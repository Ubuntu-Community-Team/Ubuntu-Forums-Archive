---
title: "White appears grayed out until compiz command run"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by jd342 on 2010-05-22
Weird issue.. When I first boot up, any white on the screen appears grayer (darker) than it should.  I found a fairly easy fix for this.  I open a terminal, type "compiz" and press enter.  The screen blinks for a second, and then when I close the terminal window, it kills the process, blinks again, then everything appears as it should.  I'm just wondering if there's a way to get around manually doing this.  

I'm running 10.04 64 bit.

Thanks

---

### Post by ubudog on 2010-05-22
There is a way.  Do this:  Hit ALT F2, type in the "command" section "gksu gedit /etc/rc.local" (without the quotes) and press enter.  Type your password in the box that comes up and press enter.  Just above the "exit 0" at the bottom of the file, type "compiz &" (without the quotes), click the save button at the top, and reboot your computer.  Now, it should automatically start.  Good luck.

---

