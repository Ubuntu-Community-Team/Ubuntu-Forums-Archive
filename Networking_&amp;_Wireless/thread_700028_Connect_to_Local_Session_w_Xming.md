---
title: "Connect to Local Session w/ Xming?"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2008-02-17
I've got Xming working and I connect using putty and command:
```
gnome-session
```
but this creates a whole NEW session...
Is there a way to connect to the local session?
Meaning if I opened up firefox locally (when I was at the keyboard), I could connect and see that same session w/ firefox on it?

TIA,
-BassKozz

---

### Post by peabody on 2008-02-18
You want vncviewer for windows.  Turn on desktop sharing in ubuntu and then you can use vncviewer to connect to a currently logged in desktop.

---

### Post by BassKozz on 2008-02-18
> **peabody said:**
> You want vncviewer for windows.  Turn on desktop sharing in ubuntu and then you can use vncviewer to connect to a currently logged in desktop.
I realize this, but I'd rather use Xming for two reasons:
[LIST=1]
[*]It's faster
[*]It's more secure because it forwards thru SSH
[/LIST]
Is it not possible to connect to the local session using SSH/X-Sessions?

---

### Post by peabody on 2008-02-18
> **B/-\ssKozz said:**
> I realize this, but I'd rather use Xming for two reasons:
[LIST=1]
[*]It's faster
[*]It's more secure because it forwards thru SSH
[/LIST]
Is it not possible to connect to the local session using SSH/X-Sessions?

TightVNC plus ssh forwarding.  Seriously not a problem.  Can use putty or cygwin ssh to do the forwarding.  Forward port 5900, connect to localhost:0.0

---

### Post by BassKozz on 2008-02-19
Ok I tried TightVNC, but it seems a tad bit slower then Xming, also clipboard interchange doesn't work;
meaning you can't copy paste to/from local/remote machines :(

---

### Post by peabody on 2008-02-19
> **B/-\ssKozz said:**
> 
Is it not possible to connect to the local session using SSH/X-Sessions?

If you're not happy with VNC, I'm pretty sure this isn't possible because Straight up X11 is a one time thing.  You can't reconnect something already connected to the local x server.

And copy and pasting can work with vnc, you just need to make sure that vncconfig is running on the remote destkop.  Go into a terminal window and run 'vncconfig' and leave it up.

---

### Post by BassKozz on 2008-03-04
Ok I've been sticking w/ VNC for the time being and I am quite happy, but I've also heard of FreeNX (and the rumors are that it is faster then VNC do to compression), will that let me connect to the local session?

---

### Post by peabody on 2008-03-04
I've heard great things about FreeNX as well, though I don't think it can be used to connect to a current logged in session.  Someone want to correct me?

---

