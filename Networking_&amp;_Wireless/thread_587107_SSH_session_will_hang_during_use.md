---
title: "SSH session will hang during use"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by funkyFlash on 2007-10-22
I'm using ubuntu 7.10, and I'm just using ssh within a gnome-terminal, and my ssh session will occasionally hang indefinitely during use.  Usually, this will come right as I exit less or vi or tail.  I will have to close the terminal and open a new one.  

The first place to point the finger would be my network admin, but another ubuntu coworker and our few mac users don't have the issue, nor our windows putty users.

What information do you need?  I don't even know where to start.

---

### Post by funkyFlash on 2007-11-15
I removed and reinstalled gnome-terminal, and openssh.  I also nuked all gnome-terminal settings.  I haven't seen the issue since, with the exception of trying to vi a 104 MB log via ssh, and I can't blame it for that.

Hope this helps somebody else.

---

### Post by sypher7 on 2008-01-16
Thanks for the tip. I was having this same issue. I reinstalled gnome-terminal and openssh, but I didn't wipe out any settings yet. It seems to have improved, we'll see if it stays that way.

Thanks again!

---

