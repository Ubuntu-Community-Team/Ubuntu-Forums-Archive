---
title: "ssh redirect running Xwindow display"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by dan_hurst on 2007-11-17
Hello all, 
I don't know if this is possible but I'm trying to remotely log into one PC from another (both running Gutsy with gnome) and redirect a currently running programs display on the remote PC to the local PC, then put it back to the original desktop before logging out.

I have SSH installed on both PCs and I can open up a terminal, SSH to the remote PC, fire up an application and then close it, which works fine.  However I just want to leave something running on one PC and remotely log in to check on its status occasionally, without restarting it and closing it down when I'm finished.

Has anyone got any ideas?

---

### Post by shad0w_walker on 2007-11-17
Whilst I believe it is theoretically possible to change the Xscreen a program is running on whilst it is still running, it is dependent on the program supporting the ability (Requires a special library to be used i belive)

The only program I'm aware of that can do this is Gimp, which is probably not what you're looking for.

---

### Post by dan_hurst on 2007-11-17
Actually, I was wondering if it was possible to do it with uTorrent running under wine.  Probably not going to work at all as its not even a linux program.

Maybe VNC would be the way to go?

---

### Post by shad0w_walker on 2007-11-17
VNC would seem to be the better way to go for that, however if memory serves utorrent has a web interface or remote control of somekind, that might be a better option if you just want to start/stop torrents.

---

### Post by dan_hurst on 2007-11-17
OMG, just got the uTorrent web interface working.  Thats amazing.  Thanks muchly.

But if anyone knows how to redirect the display of a program though I'd still like to know how to do it.

:)

---

