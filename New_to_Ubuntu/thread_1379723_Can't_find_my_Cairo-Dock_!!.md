---
title: "Can't find my Cairo-Dock !?!?"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by PepeLapiu on 2010-01-12
Okay, I installed Cairo Dock a few weeks ago but un-installed it a few days later, still it appeared to be working fine back then.

Now I re-installed it just tonight via terminal.
But when I clicked on the icon, nothing happened, so I clicked again and nothing happened again. Then I started it from the terminal and here is the result:

```
pepelapiu@pepelapiu-laptop:~$ cairo-dock -o
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-switcher.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-Dbus.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
gtk_widget_get_gl_context: assertion `GTK_IS_WIDGET (widget)' failed
OpenGL version: 2.1 Mesa 7.6
OpenGL vendor: Tungsten Graphics, Inc
OpenGL renderer: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
WARNING: Application calling GLX 1.3 function "glXCreatePbuffer" when GLX 1.3 is not supported!  This is an application bug!
if your drivers are crappy, we'll know it immediately ...do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
 ok, they seem fine enough.
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/pepelapiu/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
(null) -> -1;-1
cairo_dock_refresh_launcher_gui ()

VERIFIER LE CHANGEMENT DE CONTAINER POUR TERMINAL
```

So I looked into the System Monitor to see which processes are running. Turns out I have two instances of Cairo-Dock running but I can't find any windows or dock to that effect.

Where is my Cairo-Dock? How can I correct this problem?

Cheers,
PepeLapiu :)

---

### Post by tom.swartz07 on 2010-01-12
Im not sure how well cairo dock works with Ubuntu Netbook Remix. 

If you have the clutter launcher, it takes most of the screen. 

Is this the case?

---

### Post by PepeLapiu on 2010-01-12
I'm not sure what a "clutter launcher" is but Cairo Dock appeared to look fine when I installed it the first time around.

But right now, nothing from Cairo Dock is taking any screen space. I can't find a dock or an icon or a launcher or a widget or even a config window. Cairo Dock appears to be running in the background with no visual evidence of it at all.

---

### Post by fabounet on 2010-01-13
probably i nauto-hide, maybe behind your panel ?
try to run 
cairo-dock -m
and set adjust the visibility.
the dock works perfectly on my Dell mini9 with the openGL.

---

### Post by PepeLapiu on 2010-01-13
> **fabounet said:**
> probably i nauto-hide, maybe behind your panel ?
try to run 
cairo-dock -m
and set adjust the visibility.
the dock works perfectly on my Dell mini9 with the openGL.

Okay, I ran cairo-dock -m as you suggested and that brought up the configuration window ..... GREAT!!!!!

But only I still can't get the dock to poke out it's nose. I turned off auto-hide (which was on) but I still can't see the dock or anything else for that matter. So I thought "maybe the dock isn't showing up because it's empty so I added a few accessories and still nothing is happening.

Any other ideas? Anyway here is the terminal verbia if that can help anything:

```
pepelapiu@pepelapiu-laptop:~$ 
pepelapiu@pepelapiu-laptop:~$ cairo-dock -m
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-switcher.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-Dbus.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
atk_object_set_name: assertion `name != NULL' failed
atk_object_set_name: assertion `name != NULL' failed
atk_object_set_name: assertion `name != NULL' failed
atk_object_set_name: assertion `name != NULL' failed
atk_object_set_name: assertion `name != NULL' failed
atk_object_set_name: assertion `name != NULL' failed
atk_object_set_name: assertion `name != NULL' failed
iNbConfigDialogs <- 1
debut de boucle bloquante ...
```

---

### Post by fabounet on 2010-01-14
I would recommend to install the latest version the one in the Ubuntu repository is quite old, and a lot of work has been made since this time.
you can install it from the official PPA on Launchpad :
[https://launchpad.net/~cairo-dock-team/+archive/weekly]("https://launchpad.net/~cairo-dock-team/+archive/weekly")

Don't be afraid by the title of the page, this version is currently a release candidate, so it should be stable :-)
(deinstall it completely before to avoid any conflict)

---

### Post by PepeLapiu on 2010-01-14
Well, my Cairo Dock is back!
But the thing is, I have no idea how or why it is back. There was a problem and now it appears it fixed itself all alone, or with my unknowing help. Which kinda pisses me off because I won't know how to fix it if it happens again.

Problems and hurdles are supposed to be an opportunity to learn ....... not this time thought! :S

---

### Post by tom.swartz07 on 2010-01-14
> **PepeLapiu said:**
> Well, my Cairo Dock is back!
But the thing is, I have no idea how or why it is back. There was a problem and now it appears it fixed itself all alone, or with my unknowing help. Which kinda pisses me off because I won't know how to fix it if it happens again.

Problems and hurdles are supposed to be an opportunity to learn ....... not this time thought! :S

Perhaps it was just because the computer needed to be rebooted?
HAHA

I have docky and as amazing as it is, you have to kill it/and or reboot the computer before the new updates take hold and it stops freaking out.

---

