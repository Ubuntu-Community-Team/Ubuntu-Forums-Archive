---
title: "Karmic logs itself out . . ."
date: 2009-12-11
forum: New to Ubuntu
---

### Post by eternalnewbee on 2009-12-11
Hi guys.

I have this problem on two computers with Karmic:

Playing a game of Backbone or Solitaire, and I get logged out.

Does anyone else have this problem? . . .

. . . Does anyone know how to fix it?

Cheers.

---

### Post by musarraf172 on 2009-12-12
> **eternalnewbee said:**
> Hi guys.

I have this problem on two computers with Karmic:

Playing a game of Backbone or Solitaire, and I get logged out.

Does anyone else have this problem? . . .

. . . Does anyone know how to fix it?

Cheers.

R you running out of space? was it a fresh install? I have the same issue with upgrade. Fresh install solved my problem.

---

### Post by eternalnewbee on 2009-12-12
I have a fresh install, and I'm not running out of space, so it must be something else. 

Mind you, this is happening on two different computers . . .

---

### Post by musarraf172 on 2009-12-12
Try to reconfigure your session manager.

sudo x-session-manager dpkg-reconfigure

and also post the content of  "~/.xsession-errors" and  "/var/log/Xorg.0.log"

---

### Post by eternalnewbee on 2009-12-12
Thanks for your suggestion musarraf.

This is the outcome of *sudo x-session-manager dpkg-reconfigure*:

x-session-manager[1798]: WARNING: Unable to determine session: Unable to lookup session information for process '1798'
GNOME_KEYRING_SOCKET=/tmp/keyring-YSIeQg/socket
SSH_AUTH_SOCK=/tmp/keyring-YSIeQg/socket.ssh
GNOME_KEYRING_PID=1813

(gnome-settings-daemon:1812): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1812): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

** (gnome-settings-daemon:1812): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:1812): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
Unable to find a synaptics device.

** (gnome-settings-daemon:1812): WARNING **: Grab failed for some keys, another application may already have access the them.

** (gnome-settings-daemon:1812): WARNING **: Clipboard manager is already running.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1600x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 

(nautilus:1911): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Failed to play sound: Sound disabled
** Message: Reading of RFKILL events failed
** Message: killswitches state 3

(polkit-gnome-authentication-agent-1:1919): polkit-gnome-1-WARNING **: Unable to determine the session we are in: Remote Exception invoking org.freedesktop.ConsoleKit.Manager.GetSessionForUnixProcess() on /org/freedesktop/ConsoleKit/Manager at name org.freedesktop.ConsoleKit: org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1919' org.freedesktop.ConsoleKit.Manager.GeneralError Unable%20to%20lookup%20session%20information%20for%20process%20%271919%27

** (update-notifier:1920): WARNING **: not starting for system user

** Message: killswitches state 3

** (nm-applet:1914): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

** (gnome-panel:1910): DEBUG: Adding applet 0.
** (gnome-panel:1910): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1910): DEBUG: Adding applet 1.
** (gnome-panel:1910): DEBUG: Adding applet 2.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
** (gnome-panel:1910): DEBUG: Adding applet 3.
** (gnome-panel:1910): DEBUG: Adding applet 4.
** (gnome-panel:1910): DEBUG: Adding applet 5.
** (gnome-panel:1910): DEBUG: Adding applet 6.
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/root/.compiz/session/1010d7a72616e3b8412606321134237700000017980022"
** (gnome-panel:1910): DEBUG: Adding applet 7.
** (gnome-panel:1910): DEBUG: Adding applet 8.
** (gnome-panel:1910): DEBUG: Adding applet 9.
** (gnome-panel:1910): DEBUG: Adding applet 10.

(gnome-panel:1910): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -6 and height 24

** (nautilus:1911): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1911): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1911): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension

(nautilus:1911): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
evolution-alarm-notify-Message: Setting timeout for 30
________________________________________________________________________________________

> and also post the content of  "~/.xsession-errors" and  "/var/log/Xorg.0.log"I have no idea how to do that...

---

### Post by musarraf172 on 2009-12-12
What graphics card r you using? Did that solve your problem ? If not then boot into recovery mode and then  reconfigure your x server. and reboot the system then check the system is fine or not..

for "and also post the content of "~/.xsession-errors" and "/var/log/Xorg.0.log" "


Try to recreate the problem. Then again log in .

1. Go to your home directory. Press ctrl+h
Find the ".xsession-errors" file and open it with any text editor. Copy the content and post it here.

2. go to computer icon --> file system ---> var--->log 
find the file "Xorg.0.log" and open it with text editor and post the output here.


Alternative method:

1. Open a terminal  and execute the following commnads

" gedit ~/.xsession-errors "

"sudo gedit gedit /var/log/Xorg.0.log"

---

### Post by sandyd on 2009-12-12
seems like something is crashing X.

---

