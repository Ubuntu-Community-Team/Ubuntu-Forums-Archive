---
title: "Network manager w/o applet?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by llakais on 2010-07-30
I'd very much like to get rid of my notification tray, because everything that shows up there is either (a) pretty useless, because it stays there the whole time or (b) I have another way of interacting with.

The exception to the above is Network Manager.  I can't figure out any way to use it without having the daemon in the systray.  It's not a problem when I'm wired, but it sucks not to have it when trying to configure a wireless connection.

I even tried Wicd, since that has an "real" interface, but it was near-impossible to get it to connect to wireless networks.

Does anyone know of a way to use Network Manager without the tray - or another package that will allow me to configure connections without a tray icon?

Thanks so much for reading!

---

### Post by llakais on 2010-08-09
Anyone have any idea about this?  I'd really like to get rid of the system tray.  I'm actually trying to go completely panel-less, and Network Manger is the only thing I can't figure out how to use without panels.

Thanks!

---

### Post by Elmer Fudd on 2010-08-09
> **llakais said:**
> Anyone have any idea about this?  I'd really like to get rid of the system tray.  I'm actually trying to go completely panel-less, and Network Manger is the only thing I can't figure out how to use without panels.

Thanks!

RutilT works for me.

I go sudo panel-less just by stowing (panels/properties/"show hide buttons") them when I want to use Cairo or some other docking program.  Stowing the panels leaves a stub but that's good enough for me and gives me full access should I need it.

---

### Post by llakais on 2010-10-01
> **Elmer Fudd said:**
> RutilT works for me.

I can't seem to get this to work either.  I suppose there probably isn't anything out there as user-friendly and automated as Network Manager, that also happens to have a GUI not dependent on the panel.  Oh well.

If anyone does know of anything that works, or how to overcome problems with/setup Wicd or RutilT - please, let me know!  I will be eternally grateful!

---

### Post by andrewthomas on 2010-10-01
Maverick has cnetworkmanager - A command-line client for NetworkManager

[http://packages.ubuntu.com/maverick/cnetworkmanager](http://packages.ubuntu.com/maverick/cnetworkmanager)

---

### Post by kerry_s on 2010-10-01
wifi-radar

---

### Post by llakais on 2010-10-02
I've managed to make Wicd work (sort of), so I guess the problem is mostly solved.  I still can't figure out how to completely get rid of my panels, though.

Thanks for all your help guys, I really appreciate it.  It's awesome that so many people volunteer their time here.

---

