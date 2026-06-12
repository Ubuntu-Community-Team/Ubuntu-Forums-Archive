---
title: "VNC - No matching security types?"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by Wolfin on 2009-07-23
So here's the deal:

I have a realVNC server running at home, on my windows machine. I set it up with encryption "Always on."

Here, at another location, I try to connect to my server via a multitude of different vncviewers for Ubuntu (vncviewer, xvnc4viewer, etc) and have no luck, all of them say "No matching security types."

Where can I get a client capable of supporting RealVNC's secure protocol?

EDIT: Oh, and installing and trying to run RealVNC's viewer for linux gives me:

vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

EDIT:: Also, attempting to use the web-based, java viewer ends with nothing after I type in my VNC password.

---

### Post by superprash2003 on 2009-07-23
you would need to do this via ssh..

---

### Post by dex008 on 2009-11-04
i have the same problem before. but now i have been solved.
i succesfully install real vnc free edition for linux by downloading the dependencies. but it's not necessary to be done because later i realize that vinagre can connect to real vnc for windows too. if u use real vnc free edition for windows i think u absolutely can connect from your ubuntu, but when we use enterprise edition u must set encryption to prefer on, so our free vnc viewer can connect without encryption.

so open configure vnc server window and set encryption to prefer on, and now you can connect to your xp using your vnc viewer. :D

---

