---
title: "xming like x11 forwarding"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by Okar on 2008-11-12
Hi there,
with ssh -X you can, as you all know, forward X11 stuff, and therefor you are able to start applications on a remote machine that have a GUI.

Is there a possibility to have a complete desktop in a window like xming under windows provides you?

---

### Post by HermanAB on 2008-11-12
Usually you don't want a complete remote desktop, since you normally already have one - there is not much point in overlaying your present desktop with another - think about it for a moment.

All that you need for the remote machine is a taskbar, such as provided by Gnome or KDE:
$ ssh -X -C -c blowfish user@server gnome-panel

or
$ ssh -X -C -c blowfish user@server kicker
(Don't do this if the local machine also runs KDE3 - it will screw up)

As soon as the remote taskbar pops up on the local machine, you can go click happy and launch whatever you want remotely.

The exception is training - where you need to grab control of a remote desktop to train the user and for that VNC is good.  For everything else, SSH is better.

However, you *could* run the complete graphical desktop remotely and I have done it on occasion, if you can figure out what to run - startkde or startgnome or some such, but it will be slow and just running the taskbar alone is much better.

Cheers,

Herman

---

