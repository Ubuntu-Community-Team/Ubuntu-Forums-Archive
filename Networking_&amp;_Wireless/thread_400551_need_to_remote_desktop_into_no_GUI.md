---
title: "need to remote desktop into no GUI"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by aten on 2007-04-03
I have a computer with the ubuntu server 6.10 no Gui
i need to remote desktop connect into it, how is this possible? 
by the way the other computer will be running a form of windows xp or vista ultimate

thanks!

---

### Post by spd106 on 2007-04-03
Unless it has an X server running you won't be able to use anything like xdmcp or vnc.

For a sever it's much more common to use SSH (try installing open-ssh). You can access the ssh server via [putty]("http://en.wikipedia.org/wiki/PuTTY") from windows.

---

