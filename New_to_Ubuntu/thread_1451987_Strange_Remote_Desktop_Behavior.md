---
title: "Strange Remote Desktop Behavior"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by bpowell2005 on 2010-04-11
Hello All,

I have a bit of an odd problem:

Just upgraded to Lucid, and all is good there...however, when I start a VNC server (using tightvncserver) on the host machine (via ssh) and then VNC into it using Remote Desktop Viewer on my guest machine (Jaunty)....I get my desktop, and everything LOOKS normal...

However, when I open up a terminal, I can't use the letter "s"...Upper-case "S", no problem...lower case 's' opens up the "Logout, suspend, hibernate" menu (as if I clicked on my name in the upper right corner of the screen).

I did add this line previously to my xstartup file: export XKL_XMODMAP_DISABLE=1 which fixed a massive keyboard mis-mapping issue...but now, I just have a problem with one key, "s" which makes doing any sudo commands difficult!

Edit: The remote machine is acting like I'm hitting "Windows Key + s" which is bringing up the indicator applet (this short cut was hard-coded in Ubuntu recently)...it happens anytime I hit "s"... on Open office, Terminal...anywhere. All other keys work fine. And if I remote desktop into the main desktop (:0) everything works fine...so it's something in the vncserver setup I think.

Any ideas?

Brendan

---

### Post by bpowell2005 on 2010-04-15
Hello All,

This is still a problem for me.

I use vncserver on the host which is running 10.04. (current updates)

When I vnc into that box, I can not use the 's' key (lowercase S only)....if I type 's' then then "Log off, reboot, etc..." menu in the upper right part of my screen toggels.

What gives?!

Thanks,

Brendan

---

