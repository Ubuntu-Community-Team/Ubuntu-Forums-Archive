---
title: "VNC but no desktop"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by KeithO on 2006-11-27
I can connect to my edgy desktop from my windows box with ultravnc just fine.  however no desktop shows up when i log in.  any ideas?

---

### Post by Threbus5 on 2006-12-23
Hi,
Hmmm. If "no desktop" means that all you see is a blank screen then you may be logging in to an inactive session. Did you try using port numbers between 5900 and 5908 to find an active session?

For example the terminal window command would be "vncviewer yourhost'sIP:5900" then try "vncviewer yourhost'sIP:5901" etc.

Next, instead of typing a full command string you may try typing in the terminal window just the command:  vncviewer   and then enter the IP for the server and password as requested.

Best wishes

---

