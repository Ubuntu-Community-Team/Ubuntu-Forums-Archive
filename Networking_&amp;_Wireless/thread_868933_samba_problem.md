---
title: "samba problem"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by ikt on 2008-07-24
Hey guys, I had samba running nice and fine, now nobody can see it on the network, I am unsure where to check/test first, does anyone have any advice?

---

### Post by superprash2003 on 2008-07-24
if you are trying to connect from windows.. go to windows explorer and type \\x.x.x.x where x.x.x.x is the ip of the samba machine.. if your are trying to connect from linux then go to the terminal and type nautilus smb://x.x.x.x

---

### Post by ikt on 2008-07-24
I get a listing of my shares in ubuntu/virtual, so something must be wrong with windows xp.. anyone got any ideas >.>

Thank you for your help XD

---

### Post by ikt on 2008-07-24
Ok, incredibly simple fix, why I didn't think of.. I just use the ip address with \\ in front of in windows:

\\x.x.x.x

and it works, I can see the folders, so now my issue has become:

why is my file server not responding to its hostname?

If I do \\beta2 (the name of my file server) it says network path not found.

---

### Post by ikt on 2008-07-25
just to finish this thread, it's now working, I have no idea what changed.

---

