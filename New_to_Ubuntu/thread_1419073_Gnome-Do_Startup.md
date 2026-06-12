---
title: "Gnome-Do Startup"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by beegary on 2010-03-01
Gnome-Do used to always start up when I logged in to Karmic.

It doesnt start now. When I clcik the icon in Applications nothing happens.

When I type gnome-do into terminal i get this:

```

(/usr/lib/gnome-do/Do.exe:2391): GLib-WARNING **: g_set_prgname() called multiple times

(/usr/lib/gnome-do/Do.exe:2391): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.
```

All I did recently is add BlueMan and add a connection to my smartphone, surely this didnt break it??

---

### Post by ikt on 2010-03-01
> **beegary said:**
> Gnome-Do used to always start up when I logged in to Karmic.

It doesnt start now. When I clcik the icon in Applications nothing happens.

When I type gnome-do into terminal i get this:

```

(/usr/lib/gnome-do/Do.exe:2391): GLib-WARNING **: g_set_prgname() called multiple times

(/usr/lib/gnome-do/Do.exe:2391): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.
```

All I did recently is add BlueMan and add a connection to my smartphone, surely this didnt break it??

Are you able to kill gnome do through the system monitor and start it again?

---

### Post by beegary on 2010-03-02
I managed to get it working after playing around with start-up programs and after a couple of restarts.
Not sure what went wrong there

---

