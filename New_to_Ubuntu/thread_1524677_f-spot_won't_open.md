---
title: "f-spot won't open"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Crazedpsyc on 2010-07-05
```

(/usr/lib/f-spot/f-spot.exe:3974): GLib-WARNING **: g_set_prgname() called multiple times
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:407: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-dark.png"
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:410: Background image options specified without filename
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:416: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-dark.png"
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:419: Background image options specified without filename
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:462: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-deep.png"
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:465: Background image options specified without filename
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:471: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-deep.png"
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:474: Background image options specified without filename
/home/mike/.themes/Alien/gtk-2.0/gtkrc:1316: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-black2.png"
[Info  14:17:29.762] Initializing DBus
[Info  14:17:30.013] Initializing Mono.Addins
[Info  14:17:30.610] Starting new FSpot server (f-spot 0.6.1.5)

(/usr/lib/f-spot/f-spot.exe:3974): Gtk-WARNING **: Theme directory 22x22/action of theme kover has no size field


** (/usr/lib/f-spot/f-spot.exe:3974): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:3974): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:3974): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:3974): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:3974): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  14:17:32.354] Starting BeagleService
[Info  14:17:32.378] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:3974): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program '/usr/lib/f-spot/f-spot.exe' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2376 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```is what I get when I try to run f-spot, and it doesn't open. sorry about all the errors related to my themes! please help:-k

here are the results of f-spot --debug
```

 % f-spot --debug
** Running f-spot in Debug Mode **
** Running Mono with --debug   **

(/usr/lib/f-spot/f-spot.exe:12211): GLib-WARNING **: g_set_prgname() called multiple times
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:407: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-dark.png"
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:410: Background image options specified without filename
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:416: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-dark.png"
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:419: Background image options specified without filename
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:462: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-deep.png"
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:465: Background image options specified without filename
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:471: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-deep.png"
/home/mike/.themes/Alien/gtk-2.0/menubar-custom.rc:474: Background image options specified without filename
/home/mike/.themes/Alien/gtk-2.0/gtkrc:1316: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-black2.png"
[Info  14:39:41.184] Initializing DBus
[Debug 14:39:41.475] DBusInitialization took 0.269238s
[Info  14:39:41.475] Initializing Mono.Addins
[Debug 14:39:41.821] Mono.Addins Initialization took 0.346405s
[Info  14:39:41.836] Starting new FSpot server (f-spot 0.6.1.5)

(/usr/lib/f-spot/f-spot.exe:12211): Gtk-WARNING **: Theme directory 22x22/action of theme kover has no size field

[Debug 14:39:42.160] Db Initialization took 0.106482s

** (/usr/lib/f-spot/f-spot.exe:12211): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:12211): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:12211): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:12211): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:12211): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Debug 14:39:42.727] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 14:39:42.729] QueryToTemp took 0.001611s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 14:39:42.729] Reloading the query took 0.007462s
[Debug 14:39:42.999] PhotosPerMonth took 0.0097s
[Debug 14:39:43.006] TimeAdaptor REAL Reload took 0.239046s
[Debug 14:39:43.223] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 14:39:43.227] QueryToTemp took 0.003719s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 14:39:43.307] Reloading the query took 0.084743s
[Debug 14:39:43.313] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 14:39:43.314] QueryToTemp took 0.000979s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 14:39:43.324] Reloading the query took 0.012736s
[Info  14:39:43.339] Starting BeagleService
[Debug 14:39:43.341] BeagleService startup took 3.3E-05s
[Info  14:39:43.413] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:12211): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
[Debug 14:39:43.483] PhotosPerMonth took 0.038118s
[Debug 14:39:43.484] TimeAdaptor REAL Reload took 0.169527s
[Debug 14:39:43.530] PhotosPerMonth took 0.012337s
[Debug 14:39:43.530] TimeAdaptor REAL Reload took 0.216052s
The program '/usr/lib/f-spot/f-spot.exe' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2376 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

---

### Post by jtarin on 2010-07-05
Has it ever started before or is this a new install? How did you install, by what method? You might try uninstalling then reinstall using synaptic.
You might have unresolved dependencies.

---

### Post by Crazedpsyc on 2010-07-06
I installed with synaptic, it is the first time I have installed in this version, I had it in 9.04 working fine. I checked dependencies and recommendeds but all are installed

---

### Post by philinux on 2010-07-06
> **Crazedpsyc said:**
> I installed with synaptic, it is the first time I have installed in this version, I had it in 9.04 working fine. I checked dependencies and recommendeds but all are installed

Change your theme in Sys>prefs >appearance.

Looks like a problem with alien theme.

---

### Post by Crazedpsyc on 2010-07-06
Ok, thanks but howcan i fix that prob, since Alien is my theme (I'm making it)

---

### Post by philinux on 2010-07-06
> **Crazedpsyc said:**
> Ok, thanks but howcan i fix that prob, since Alien is my theme (I'm making it)

Look at the error messages in your first post.

---

### Post by Crazedpsyc on 2010-07-07
so I just need to put those files mentioned back right? Ok I thought they were useless because in the theme I built this one on it had those in there just so you could choose, but whatever, maybe I can tell it not to look for those, so  I don't have to make it bigger.

---

