---
title: "VNC client that establishes ssh tunnel?"
date: 2019-10-14
forum: Networking &amp; Wireless
---

### Post by Markardi on 2019-10-14
Hi,

Currently running 18.04 desktop version as server.  Have to reinstall/reconfigure most things after a broken 16.04 upgrade.
I've reinstalled a VNC server, openssh, and fail2ban.  On a Windows 10 system, I installed the openssh client.

Currently, to remote desktop into the server from a Windows 10 machine, I have to use power shell to establish the ssh connection, then I can use a vnc client to get a GUI.

Are there any VNC Clients that can establish the ssh tunnel so I don't have to do it from power shell first?
Or is there something that needs to be configured in the openssh client on Win 10?

TightVNC Java Viewer states that it supports built-in SSH tunneling, but as my system doesn't have Java RE installed, that not an option. (also, I won't install Java)

I installed the non java client on Win 10, but I don't see any obvious way to configure it to establish the ssh connection.

Thanks,
Mark

---

### Post by Skaperen on 2019-10-14
are you asking for something to run on Windows?  if so, i think you will get better answers by asking in a Windows forum.

---

### Post by Markardi on 2019-10-15
Fair enough!

---

### Post by TheFu on 2019-10-15
If you are trying to have the desktop displayed on a Windows machine, but connected to a remote Linux machine, the easiest way to accomplish that is to use x2go.  x2go uses the NX protocol which leverages ssh and honors ssh-keys, authentication, etc.  Install the x2go-server on the remote Ubuntu machine using the PPA for it. Install the x2go client on the Windows machine - be certain to get all the fonts - usually in a different download.

The only negative for x2go is that the clients only work on Linux, Windows, OSX and that only light DEs are supported. Basically, anything that isn't Gnome3.  LXDE, KDE, XFCE, Mate all work well.  The 'server' only works on Linux.  

x2go feels 2-3x faster than any VNC.  A single GUI on the client handles the tunnel + GUI settings.

I see people here struggling to use VNC all the time. I point them towards x2go and about 30% make the switch, happily.

---

