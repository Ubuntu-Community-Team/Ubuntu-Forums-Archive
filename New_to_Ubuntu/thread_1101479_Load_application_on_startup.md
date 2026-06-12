---
title: "Load application on startup?"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-03-20
Hi all,

1st install has gone well and am pretty impressed thus far...getting into the nuts and bolts of it now and have a query - 

How can I configure an app (specifically in this case Transmission torrent client) to load as soon as I start up?

Cheers
Kyle

---

### Post by rburkartjo on 2009-03-20
aqua, got to system/pref/sessions (note might be called startup appl) either way open it click on add and paste under name the following
Transmission BitTorrent Client

the under command paste the following
transmission %F

there is a comment line (you dont have to enter anything there)

click add and that is it should auto start when you login or startup. let me know how it goes it is the same way to add program to startup the name and command just changes

---

### Post by aquascrotum on 2009-03-20
Cheers - is there any way to make it start minimised to the system tray (for apps that can run from the tray, torrent, firestarter etc

---

### Post by issih on 2009-03-20
If you launch transmission with a -m option in the command, i.e.

```
transmission -m
```

it should start in the tray.

Hope that helps

P.S. if you enter "transmission --help" into a terminal, it will tell you what some of the simpler command line options do...this will generally work for other apps too, so just do that for anything else you'd like to launch minimised and see what option flags are available.

---

