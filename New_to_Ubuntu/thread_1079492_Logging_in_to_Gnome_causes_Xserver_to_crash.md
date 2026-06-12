---
title: "Logging in to Gnome causes Xserver to crash"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by rossjman1 on 2009-02-24
Last night, I was messing around with Nautilous options and I changed the zoom to 200% and the xserver crashed. Now every time I try to log into Gnome it crashes after 30 seconds or so.

Here is my .xessionerrors:
> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[5662]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2800x1050) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
gnome-session[5662]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:5839): WARNING **: Unable to add monitor: Not supported
gnome-session[5662]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout

(avant-window-navigator:5879): Gtk-WARNING **: cannot open display: :0.0

(xdg-user-dirs-gtk-update:5882): Gtk-WARNING **: cannot open display: :0.0
Cannot open display: 
Cannot open display: 
Run 'gnome-power-manager --help' to see a full list of available command line options.
Cannot open display: 
Run 'update-notifier --help' to see a full list of available command line options.
E: client-conf-x11.c: XOpenDisplay() failed
Failure: Module initalization failed

(nm-applet:5887): Gtk-WARNING **: cannot open display: :0.0

(evolution-alarm-notify:5881): Gtk-WARNING **: cannot open display: :0.0
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: Warning: invalid (NULL) pointer instance
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: _gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: gdk_drawable_get_display: assertion `GDK_IS_DRAWABLE (drawable)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: gdk_x11_get_xatom_by_name_for_display: assertion `GDK_IS_DISPLAY (display)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: /build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
/usr/lib/python2.5/site-packages/FusionIcon/interface_gtk/main.py:206: GtkWarning: gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
  icon = gtk.status_icon_new_from_icon_name('fusion-icon')
Conky: can't open display: :0.0

---

### Post by rossjman1 on 2009-02-24
bump

---

### Post by philinux on 2009-02-24
Login as normal. Open a terminal and try this.

```
metacity --replace
```

It's also bad form to bump so quickly.

---

### Post by rossjman1 on 2009-02-24
I can't get Metacity to run because Gnome crashes right away. I have homework and stuff I have to do so I would like this to be fixed sometime today.

---

### Post by rossjman1 on 2009-02-24
bump

---

### Post by rossjman1 on 2009-02-24
```

rm -r ~/.nautilus
```
fixed my problem.

---

