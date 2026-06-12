---
title: "problem with ssh -X"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by outleradam on 2010-10-25
Usually I just ssh -X and gedit things on my media center.  

Since I upgraded to maverick, I get this:
```
root@XBMC-live:~# gedit

** (gedit:1936): WARNING **: Could not load theme icon gtk-home: Icon 'gtk-home' not present in theme

(gedit:1936): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (gedit:1936): WARNING **: Could not load theme icon system-file-manager: Icon 'system-file-manager' not present in theme
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtkrecentmanager.c:1942:get_icon_fallback: assertion failed: (retval != NULL)
Aborted
```The gedit window flashes on screen, then goes away.  What can I do?  I assume it's looking for some sort of gay icon pack... I don't know how to install it.

---

### Post by carl.davis on 2010-10-26
Hello,

Can you try changing themes and see if this helps? If you try to run gedit locally do you get the same error?

 Although this post talks about the same error, I am not sure it is a related problem if you can run gedit locally.

[http://ubuntuforums.org/showthread.php?t=1604385](http://ubuntuforums.org/showthread.php?t=1604385)

---

### Post by outleradam on 2010-10-26
Yes.  I can run gedit locally.  I'm trying to run it remotely from another X server.  I only have an X interface on that server.  There is no desktop. It is only xinit running XBMC.  There should not be a theme installed.  

How can I install a theme without a desktop?

---

### Post by carl.davis on 2010-10-26
If you can run gedit locally I am not sure that changing the theme will help. I was unable to duplicate this error using ssh -X to a 10.04 machine. What is your media center running?

---

### Post by outleradam on 2010-10-30
10.10
Linux XBMC-live 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

Dosn't it pull the icons for the theames from the X interface host computer?

---

### Post by outleradam on 2010-10-30
xclock works just fine

gedit just gives me errors

```
root@XBMC-live:~# gedit

** (gedit:26998): WARNING **: Could not load theme icon gtk-home: Error opening file: No such file or directory

(gedit:26998): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (gedit:26998): WARNING **: Could not load theme icon system-file-manager: Icon 'system-file-manager' not present in theme
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtkrecentmanager.c:1942:get_icon_fallback: assertion failed: (retval != NULL)
Aborted
root@XBMC-live:~#
```

I really could use some help on this.

---

### Post by outleradam on 2010-10-30
Is there anything that can be done about this?

---

### Post by Stoneface on 2011-02-05
> **outleradam said:**
> xclock works just fine

gedit just gives me errors

```
root@XBMC-live:~# gedit

** (gedit:26998): WARNING **: Could not load theme icon gtk-home: Error opening file: No such file or directory

(gedit:26998): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (gedit:26998): WARNING **: Could not load theme icon system-file-manager: Icon 'system-file-manager' not present in theme
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtkrecentmanager.c:1942:get_icon_fallback: assertion failed: (retval != NULL)
Aborted
root@XBMC-live:~#
```

I really could use some help on this.

I am having similar issues atm. Gedit crashes all the time:
```
$ gedit


** (gedit:60747): WARNING **: Could not load theme icon gtk-home: Icon 'gtk-home' not present in theme

(gedit:60747): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (gedit:60747): WARNING **: Could not load theme icon system-file-manager: Icon 'system-file-manager' not present in theme
**
Gtk:ERROR:gtkrecentmanager.c:1942:get_icon_fallback: assertion failed: (retval != NULL)
Abort trap
```

I also found: [https://bugs.launchpad.net/ubuntu/+bug/669572](https://bugs.launchpad.net/ubuntu/+bug/669572) . I think it is a GTK/Gnome issue. No solution yet though. Did you manage to fix this issue yet?

---

