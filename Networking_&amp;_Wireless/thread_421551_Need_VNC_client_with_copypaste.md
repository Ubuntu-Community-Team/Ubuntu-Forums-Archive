---
title: "Need VNC client with copy/paste"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by NiksaVel on 2007-04-24
Hey guys... I'm succesfully using the Terminal Server Client program for VNCing among my computers.. but it seems to lack one VERY important function - the copy/paste between computers doesn't work...


Quite often I need to manually retype lengthy URLs and such..


Is there some simple VNC viewer that will make my life easier?

---

### Post by deadlines on 2007-04-24
Install [gnome-rdp]("http://gnome-rdp.linuxforge.hu"), it supports copying and pasting from RDP sessions.  Beware though, this sometimes causes applications to hang for a bit when pasting data copied from a RDP session into a local app, not always though.  Overall it works much better than Terminal Server Client for my needs.

P.S. This app is in the Ubuntu repos so no need to compile.

---

### Post by SeanHodges on 2007-07-11
I use gnome-rdp and I'm still not able to copy-paste from my machine to the remote machine, or visa-versa. Is there anything I need to do to enable this?

Also, has anyone managed to get gnome-rdp to work in the gnome session start-up? I have the following set-up:

System -> Preferences -> Sessions --> "Startup Programs" tab

Added "gnome-rdp --start-hidden" (without quotes) to "Additional startup programs" box


It doesn't matter if I remove --start-hidden from the command, it still doesn't seem to start gnome-rdp automatically.

---

### Post by dustrho on 2007-07-11
I use Gnome-RDP as well, but the whole copy/paste feature doesn't work for me when trying to copy text from a remote session (Windows Server) to any application on my Ubuntu box. I read above that the copy/paste feature should work for this, but it doesn't. Hope someone has the answers to this.

---

### Post by tcpip4lyfe on 2007-07-11
I'f you going to a windows box have you tried this?:

[http://cutecomputer.wordpress.com/2007/01/03/howto-copy-paste-between-local-and-remote-desktop/](http://cutecomputer.wordpress.com/2007/01/03/howto-copy-paste-between-local-and-remote-desktop/)

---

