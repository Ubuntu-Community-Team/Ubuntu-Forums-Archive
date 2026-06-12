---
title: "gnome-settings-daemon"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by xaegis on 2009-10-20
Hello all.
I did a search and came up 0.

My gnome settings daemon is now refusing to retain settings.

I get this error.

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

Anyone have any ideas on what i can do?
Running a fresh 9.10 install.

Thanks in advance.

---

### Post by bodhi.zazen on 2009-10-20
Did you install KDE ?

Try running gnome-settings-daemon from the command line and see if you get any further clues.

```
sudo gnome-settings-daemon
```

---

### Post by xaegis on 2009-10-20
Thanks for helping with this.
I tried to start the daemon in terminal and get:
```

(gnome-settings-daemon:6460): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:6460): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

```

thanks again!

---

### Post by bodhi.zazen on 2009-10-20
See if this helps at all :

[https://bugs.launchpad.net/gstreamer/+bug/384439](https://bugs.launchpad.net/gstreamer/+bug/384439)

I assume you are running karmic ?

---

### Post by xaegis on 2009-10-20
I'm running jaunty not karmic.

I have some Qt apps but kde is not installed fully.(ie dolphin etc.) 
 
i uninstalled gstreamer0.10-ffmpeg and still no love.

=(

---

