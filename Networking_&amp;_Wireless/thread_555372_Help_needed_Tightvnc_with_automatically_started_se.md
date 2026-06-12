---
title: "Help needed: Tightvnc with automatically started sessions"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by BatPenguin on 2007-09-20
Hello everybody,

I've been searching the forums for information of how to setup Tightvnc for a while and can't seem to find much about actually setting up sessions for it. There's plenty of stuff about VNC and XDMCP, both useful I'm sure, but I'd like to use Tightvnc for its supposed better speed. I'll be using the server from a laptop connecting with just a WLAN connection and I'd like to get as close to "normal" speed as possible on the display.

So far I've managed to install Tightvnc simply by apt-getting tightvncserver and xtightvncviewer. I've also added

```
gnome-session &
```

into my ~/.vnc/xstartup

and this is enough to get Gnome started when I launch tightvncserver either by itself or with a few -depth or -resolution switches.

Now doing either a local vncviewer localhost or a connection from a remote machine, I can get in and view the desktop, but the problem is the resolution. Regardless of what I set in the tightvncserver command, it doesn't seem to change the actual screen resolution of the session but only the window size. All connections will start with a window of the specified size (such as 1024 x 768 ) but the actual resolution inside that window is my normal desktop resolution - too large for these clients, which means I'll have to scroll the display to see it. The speed doesn't seem too great either, but I suspect this might be because of 24 bit colors -- and I'm trying to use 16 for speed but I don't think it's working.

So: could anybody help me setup a few auto-start sessions at bootup at pre-defined resolutions? I don't really care it they are resumable or not, and whether it's the same desktop user or not (I can make extra accounts for each vnc client, totally fine). I just want to be able to have a FAST VNC connection to the server.

In some other distros (Fedora) I think this is done using a /etc/sysconfig/vncservers file. Ubuntu doesn't have this. How would I do this? Using tightvnc is important for me as I'd really like to get the speed as good as possible. Thanks!

---

