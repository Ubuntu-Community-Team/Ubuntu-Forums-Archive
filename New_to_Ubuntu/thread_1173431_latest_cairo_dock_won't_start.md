---
title: "latest cairo dock won't start"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by enri2 on 2009-05-29
won't start. only the one on the repository starts  which is an old version 1.6 (or something)  i need the latest because i wan't the leopard reflective dock/bg

any idea why it doesn't start ??

---

### Post by Viva on 2009-05-29
Open it using terminal and post the error. are you trying to open the OpenGl version or the non-opengl one?

---

### Post by enri2 on 2009-05-29
I have no idea how to open it in terminal  and no idea  what version I'm using??  I usualy start it  with alt-f2 .... can you tell me more??

---

### Post by enri2 on 2009-05-29
i got it from here 
[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

---

### Post by enri2 on 2009-05-29
never mind  i downloaded different version than my machine can suport. got it working now.

---

### Post by Viva on 2009-05-29
Open Applications->Accessories->Terminal and type

```
cairo-dock -c
```

Then do the same with this code

```
cairo-dock -o
```

EDIT: Glad you got it fixed

---

### Post by letsflyakite on 2009-07-15
hi I had the same problem, the dock wouldn't start. I install it by double clicking the installation .deb file.

I am new to Linux, can any one help look at the below and let me know what's the issue and how to fix it?

many thanks.


**$ cairo-dock -c**
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:505)  
  The option 'auto-hide on fullsecreen window' is in conflict with the accessibility options, it will be deactivated
g_strsplit: assertion `string != NULL' failed
g_strsplit: assertion `string != NULL' failed
cairo_dock_duplicate_surface (112.00x112.00 -> 96.00x96.00)
on positionne la miniature de Terminal
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (dialog rendering)
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (clock)
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (Dbus)
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (dustbin)
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (dock rendering)

**$ cairo-dock -o**
gtk_widget_get_gl_context: assertion `GTK_IS_WIDGET (widget)' failed
OpenGL version: 2.1.2 NVIDIA 169.12
OpenGL vendor: NVIDIA Corporation
OpenGL renderer: Quadro NVS 140M/PCI/SSE2
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:505)  
  The option 'auto-hide on fullsecreen window' is in conflict with the accessibility options, it will be deactivated
g_strsplit: assertion `string != NULL' failed
g_strsplit: assertion `string != NULL' failed
cairo_dock_duplicate_surface (112.00x112.00 -> 96.00x96.00)
on positionne la miniature de Terminal
if your drivers are crappy, we'll know it immediately ... ok, they seem fine enough.
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (dialog rendering)
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (clock)
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (Dbus)
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (dustbin)
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:374)  
  No such module (dock rendering)

---

### Post by Viva on 2009-07-15
Try installing cairo-dock modules.

---

### Post by fabounet on 2009-07-16
use the repository to avoid plateform/version mismatch
plus you will stay up to date automatically.

---

### Post by OrangeChrome on 2011-01-22
Hey folks I'm having a similar error after doing some troubleshooting with my Video drivers for a Radeon 9000 Pro - which was unsuccessful.  

I ran:
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
To disable KMS. 
Rebooted - Video was much worse
I then ran:  echo options radeon modeset=1 > /etc/modprobe.d/radeon-kms.conf
To re-enable KMS
Rebooted again. Everything ran fine but I didn't have my Cairo Dock

I can open CairoDock without openGL but it runs like garbage.  From what I understand it's because it's all software - no hardware accel.

Anyways, so don't yell at me too much cause *I KNOW* that I'm pretty much a linux n00b.  Any help would be greatly appreciated.

$ cairo-dock
Segmentation fault
$ cairo-dock -c

 ============================================================================ 
    Cairo-Dock version: 2.2.0-4
    Compiled date:  Oct  7 2010 21:24:32
    Running with OpenGL: 0
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.2.0~4/src/gldit/cairo-dock-modules.c:cairo_dock_load_modules_in_directory:400)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (/build/buildd/cairo-dock-2.2.0~4/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:656)  
  while listing user packages in '/home/globe/.config/cairo-dock/third-party' : Error opening directory '/home/globe/.config/cairo-dock/third-party': No such file or directory
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
^C
$ cairo-dock -o
Segmentation fault

Also - Wanted to note that I tried re-installing cairo-dock and all associated packages via the synaptics package manager - no luck.  I'm guessing some kind of config-file got corrupted or something.  Not sure.. ?

---

### Post by Razzl3Dazl3 on 2011-02-07
I need a bit of help as well. tried to modify the them of the dock and it went away. unable to get back working even after purge, uninstall, and re-install. this is the error I'm getting. just got Ubuntu 10.10. any help or advise is greatly appreciated.

 ============================================================================ 
    Cairo-Dock version: 2.2.0-4
    Compiled date:  Oct  1 2010 22:56:27
    Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.2.0-4/src/gldit/cairo-dock-modules.c:cairo_dock_load_modules_in_directory:400)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
cairo_dock_create_surface_from_image: assertion `cImagePath != NULL' failed
warning :  (/build/buildd/cairo-dock-2.2.0-4/src/gldit/cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:418)  
  This file (/home/jared/.icons/Leopard_Icons_v0.3/EXTRAS/More/QuickTimePlayer.png) doesn't exist or is not readable.

---

