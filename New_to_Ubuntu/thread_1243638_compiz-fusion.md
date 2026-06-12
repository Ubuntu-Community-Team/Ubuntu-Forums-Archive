---
title: "compiz-fusion"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by andres-bracho on 2009-08-18
Hi,

I installed a game (yo frankie) but since I didn't like it I remove it... since then I'm unable to start compiz, if I go to "Apariencia" (sorry my Ubuntu is in Spanish... I mean that window where you change your desktop theme, icons, etc. and start your compiz) and check the Extra option in Visual effects, my screen blinks but shows a message saying that it can't start compiz...

I typed compiz on a console and this was the result:
andres@MegaMovil:~$ compiz
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Advertencia del gestor de ventanas: Ocurrió un error al leer el archivo de sesión guardado
*/home/andres/*.config/metacity/sessions/104395ce385d0d1f07125053332749486800000032680005.ms: Ha ocurrido un error al abrir el archivo
«*/home/andres/*.config/metacity/sessions/104395ce385d0d1f07125053332749486800000032680005.ms»:·No existe el fichero ó directorioAt the same time, each time that I turn off my computer in front of AWN a popup window appear saying that there is no "composite" or something like this.

Today I tried to start AWN from console and this was I received:
aandres@MegaMovil:~$ awn
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/cairo_main_menu.desktop
APPLET : /usr/share/avant-window-navigator/applets/file-browser-launcher.desktop
APPLET : /usr/share/avant-window-navigator/applets/awnterm.desktop
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/thunderbird.desktop
LOADED : /usr/share/applications/liferea.desktop
LOADED : /usr/share/applications/transmission.desktop
LOADED : /usr/share/applications/calibre.desktop
LOADED : /home/andres/.local/share/applications/openoffice.org-startcenter.desktop
LOADED : /home/andres/.local/share/applications/Picasa.desktop
LOADED : /usr/share/applications/audacious.desktop
LOADED : /usr/share/applications/vlc.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop

(awn-applet-activation:4295): Vte-CRITICAL **: vte_terminal_set_background_image_file: assertion `VTE_IS_TERMINAL(terminal)' failed

(awn-applet-activation:4295): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.20.1/gobject/gsignal.c:2349: handler `50' of instance `0x9598010' is not blocked

(awn-applet-activation:4288): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `icon_name != NULL' failed

(awn-applet-activation:4288): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `filename != NULL' failed

This is an Acer Aspire 9300, AMD64, Athlon X2, 1.7 Ghz, 2x256 Kb L2 Cache, 80 Gb HD and 2 Gb DDR2 with a NVIDIA GeForce Go 6100 528 Mb.

Thanks in advance.-

---

### Post by LowSky on 2009-08-18
in a terminal type

```
compiz --replace
```

---

### Post by andres-bracho on 2009-08-18
:(

andres@MegaMovil:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

