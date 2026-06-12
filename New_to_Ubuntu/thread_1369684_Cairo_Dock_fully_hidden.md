---
title: "Cairo Dock fully hidden"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Indigo340 on 2010-01-01
I have a problem with Cairo Dock, I reduced the number of pixels at the bottom of the screen so the dock was lower down by -10 pxls and then enabled 'Auto Hide' and now cannot 'Un-hide' it !
I selected the 'show dock' area to be 2 pixels (up from 1 pxls) but I probably should have added those pixels that I subtracted when I moved the dock down by -10 pxls.
Now I can't 'un-hide' the dock ! I have tried uninstalling and re-installing it and have tried to use the command 'cairo-dock --keep-above' but I get the following errors and warnings in Terminal;
ian@ian-laptop:~$ cairo-dock --keep-above
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-Dbus.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-switcher.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
gtk_widget_get_gl_context: assertion `GTK_IS_WIDGET (widget)' failed
OpenGL version: 2.1.2 NVIDIA 185.18.36
OpenGL vendor: NVIDIA Corporation
OpenGL renderer: GeForce Go 7400/PCI/SSE2
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:132)  
  Can't have thumbnail for a window that is minimized when the dock is launched.
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:132)  
  Can't have thumbnail for a window that is minimized when the dock is launched.
if your drivers are crappy, we'll know it immediately ... ok, they seem fine enough.
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/ian/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
size : applet : 96, image : 100
 + needle 96x10
cd_sysmonitor_get_cpu_data: assertion `fTimeElapsed > 0.1' failed
Binding '<Shift>F1' failed!
warning :  (cairo-dock-keybinder.c:cd_keybinder_bind:303)  
  couldnt bind <Shift>F1
Binding '<Shift>F2' failed!
warning :  (cairo-dock-keybinder.c:cd_keybinder_bind:303)  
  couldnt bind <Shift>F2
1 -> 1;-1
cairo_dock_refresh_launcher_gui ()

VERIFIER LE CHANGEMENT DE CONTAINER POUR TERMINAL

And the process appears to be running but it's not doing anything!
How can I get Cairo Dock back ? PLEASE HELP !

Sony Vaio laptop, 2 X 1.6GHZ, 2gig RAM, GeForce 7400 GO. Karmic

---

### Post by chaanakya_chiraag on 2010-01-01
If it is not too much of a hassle, try removing any folder which looks remotely like Cairo Dock's.  Go to your home folder and hit Ctrl-H to display hidden files.  Now scroll through and look for .cairodock or something like that.  Also look in the .config folder.  **Please remember that you will lose all of your settings in Cairo Dock after deleting that folder.**  But it should get you your dock back :D

---

### Post by Indigo340 on 2010-01-01
OK thanks for the quick reply, I'll give it a try, I presume you mean after uninstalling it.

I just checked and there is no folder with a name like that

---

### Post by Indigo340 on 2010-01-01
It's getting worse, now I can't open Synaptic !

Is there a way to get back to how it was yesterday ?

---

### Post by chaanakya_chiraag on 2010-01-01
Hmmm...did you delete any files at all?  Something seems very weird if, soon after Cairo Dock stops working, Synaptic also stops working.  What error does it give you?

---

### Post by Indigo340 on 2010-01-01
I found the Cairo Dock files in .config and deleted them first then had a problem with Synaptic but have got Synaptic back now using Terminal.
I then used Synaptic to download  Cairo Dock again but it does not appear in the menu so can't enable it, i really got to to like CD and want it back but seems like I have lost it :-(

---

### Post by fabounet on 2010-01-01
```
cairo-dock -m
```
to get the config manager displayed, then modify what you want, apply, and close the window ;)

---

### Post by Indigo340 on 2010-01-02
Thanks a lot fabounet ! It took a couple of tries but I got there in the end.  It was very good of you to help, thanks again !

---

### Post by Indigo340 on 2010-01-03
There is a small issue now. I have CD fully operational and am very happy again but now when I start the laptop I can see a small panel on the desktop in the top left corner which says "Try to steal systray icons" it wasn't there before and if I click on it, it disappears without starting any action ! Can you explain this to me and how to get rid of it ?

---

### Post by fabounet on 2010-01-03
this is the systray
wince you can't have 2 systray on an X desktop, it asks you to steal the existing systray (probably the one of your gnome-panel)

---

