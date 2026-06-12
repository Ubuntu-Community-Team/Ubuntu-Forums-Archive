---
title: "Cairo Dock Crashes"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-05-15
When I try to launch Cairo Dock, the dock doesn't appear and the Maintenance Window pops up. This happens when I try to launch either the GLX or the no opengl version from the Gnome Menu.

Here's what happens when I try to launch it from the terminal:

```

~$ cairo-dock -c
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:319)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
myLabels.iLabelSize : 22 -> 23
Fontconfig error: "~/.fonts.conf", line 1: no element found
g_strsplit: assertion `string != NULL' failed
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:171)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:171)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/timothycbautista/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
cairo_dock_replace_key_values (0)
cairo_dock_create_surface_from_image: assertion `cImagePath != NULL && pSourceContext != NULL && cairo_status (pSourceContext) == CAIRO_STATUS_SUCCESS' failed
warning :  (cairo-dock.c:_cairo_dock_intercept_signal:195)  
  Cairo-Dock has crashed (sig 11).
It will be restarted now.
Feel free to report this bug on cairo-dock.org to help improving the dock !
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:319)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
Fontconfig error: "~/.fonts.conf", line 1: no element found
debut de boucle bloquante ...

```

```

~$ cairo-dock -c
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:319)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
myLabels.iLabelSize : 22 -> 23
Fontconfig error: "~/.fonts.conf", line 1: no element found
g_strsplit: assertion `string != NULL' failed
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:171)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:171)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/timothycbautista/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
cairo_dock_replace_key_values (0)
cairo_dock_create_surface_from_image: assertion `cImagePath != NULL && pSourceContext != NULL && cairo_status (pSourceContext) == CAIRO_STATUS_SUCCESS' failed
warning :  (cairo-dock.c:_cairo_dock_intercept_signal:195)  
  Cairo-Dock has crashed (sig 11).
It will be restarted now.
Feel free to report this bug on cairo-dock.org to help improving the dock !
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:319)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
Fontconfig error: "~/.fonts.conf", line 1: no element found
debut de boucle bloquante ...

```

Should I report this in a bug report?

---

### Post by fabounet on 2009-05-16
can you launch it with ddd ?
ddd cairo-dock

if you don't have the sources, then you may try cairo-dock -Tc -l debug
it may give some clue.
thanks.

Edit : if you want to get rid of the problem, you might want to delete ~/.config/cairo-dock/current_theme, and restart the dock
but you'll loose your current theme then.

---

