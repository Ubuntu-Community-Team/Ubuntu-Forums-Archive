---
title: "SSH X11 Forwarding again"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by duskie on 2007-03-09
Ok, as I see, a bit problematic area.

I am running Xubuntu Edgy, OpenSSH server, and X.org accepting remote connections. 

I can connect to my machine with X11 forwarding working fine, from work, from MacOS X with X11. I can open X applications, everything works fine.

But when I want to connect from my home, Ubuntu machine, to my friend's machine, which is also running Ubuntu with sshd, and X11, a problem appears. I run 

ssh -Y -C -vvv me@myfriend

no errors, everything looks fine, .Xauthority file created, $DISPLAY variable set properly to localhost:10.0

now:

$ xclock

a new window appears on my desktop, with icon of a clock, but whoops, nothing inside, I click close, but terminal won't let me back to shell, a pressed Ctrl+C, nothing happens. Veeeery strange. Any suggestions?

---

