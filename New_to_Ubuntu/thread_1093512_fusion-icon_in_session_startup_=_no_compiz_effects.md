---
title: "fusion-icon in session startup = no compiz effects"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by arapa on 2009-03-11
When I have the fusion-icon added to load at start-up, the compiz effects are being turned off (I assume crashes compiz-fusion). On load there is a quick flicker right before the icon shows on the panel (not sure if it is related to the problem).

I can turn compiz effects back on once everything loads and everything works. I can also load the fusion-icon (with compiz effects on) after the session is fully up and running with no problems. My problem is getting both compiz effects and the fusion-icon to load at start-up automatically.

Has anyone else had this problem? Is there a file that needs modified that changes the load order? Any help would be appreciated.

---

### Post by LowSky on 2009-03-11
press Alt+F2 type 
```
compiz --replace
```

now with the fusion-icon started hit refresh, it should stay on compiz, if not then its loading metacity as the default asnd we dont wna that.

from now on it shouldn't be an issue

---

### Post by arapa on 2009-03-11
Thanks for the reply. I entered the '--replace' command and then clicked the "reload window manager". The compiz effects did turn on after that  but when I reboot or log out / log back in, the compiz effects don't work unless I manually go to the fusion-icon and click "reload window manager", then they work. If I don't load the fusion-icon at start-up, compiz works at start-up without having to reload it.

This is what shows up in my syslog after logging out/logging in: 

```
Mar 11 19:25:22 ubu64 acpid: client connected from 7573[0:0] 
Mar 11 19:25:24 ubu64 acpid: client connected from 7573[0:0] 
Mar 11 19:25:32 ubu64 pulseaudio[7693]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 11 19:25:32 ubu64 pulseaudio[7695]: pid.c: Stale PID file, overwriting.
Mar 11 19:25:32 ubu64 pulseaudio[7695]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 11 19:25:32 ubu64 pulseaudio[7695]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 11 19:25:32 ubu64 x-session-manager[7607]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Mar 11 19:25:32 ubu64 x-session-manager[7607]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Mar 11 19:25:42 ubu64 x-session-manager[7607]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Mar 11 19:25:52 ubu64 x-session-manager[7607]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Mar 11 19:25:53 ubu64 pulseaudio[7695]: module-x11-xsmp.c: X11 session manager not running.
Mar 11 19:25:53 ubu64 pulseaudio[7695]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
```

---

### Post by Therion on 2009-03-11
Try this...

System/Preferences/Sessions
Open "Starup Programs" and click on the "Add" button.

Name: Whatever you want to call it.
Command: **compiz --replace**
Comment: Optional.  No real need.

Click "OK" and make sure the new entry in the list has a tic in it's box.
Log out, log back in... Check to see if Compiz is running the show.

---

### Post by arapa on 2009-03-11
Thanks Therion, I added the command to the sessions startup program but with the same result.

---

### Post by DownTown22 on 2009-03-11
I can't offer any help, but I have the exact same problem.

I have fusion icon set to start up automatically when I boot up, and every time, compiz isn't being loaded by default.  I have to click the fusion icon and tell it to reload the window manager, after that it works.

Kind of annoying every time I boot my computer I have to tell it to reload.

This only started happening after I installed the fusion icon.

---

### Post by arapa on 2009-03-15
OK - I managed to solve this one.

When adding the fusion-icon to the sessions preferences (system>preferences>sessions) I needed to add --no-start to the start-up command:
```

fusion-icon --no-start
```

instead of just /usr/bin/fusion-icon.

The flash I was seeing right before the icon appeared was fusion-icon defaulting to trying to start the windows manager (which was already started).

The --no-start option will just load the icon.:D

---

### Post by DownTown22 on 2009-03-15
Nice work!

Will give it a go whenever I get home.

---

### Post by josephb on 2009-05-03
> **arapa said:**
> OK - I managed to solve this one.

When adding the fusion-icon to the sessions preferences (system>preferences>sessions) I needed to add --no-start to the start-up command:
```

fusion-icon --no-start
```

instead of just /usr/bin/fusion-icon.

The flash I was seeing right before the icon appeared was fusion-icon defaulting to trying to start the windows manager (which was already started).

The --no-start option will just load the icon.:D

Works for me. Much Thanks.
:)

---

### Post by MastroPino on 2009-09-04
> **arapa said:**
> OK - I managed to solve this one.

When adding the fusion-icon to the sessions preferences (system>preferences>sessions) I needed to add --no-start to the start-up command:
```

fusion-icon --no-start
```

instead of just /usr/bin/fusion-icon.

The flash I was seeing right before the icon appeared was fusion-icon defaulting to trying to start the windows manager (which was already started).

The --no-start option will just load the icon.:D

:popcorn: thanks!

---

