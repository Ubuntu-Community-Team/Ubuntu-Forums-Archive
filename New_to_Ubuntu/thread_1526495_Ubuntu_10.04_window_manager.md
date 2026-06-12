---
title: "Ubuntu 10.04 window manager???"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by C4BL3 on 2010-07-08
Greetings comrades. 

So, I just installed Ubuntu 10.04 and everything worked fine until I installed and then uninstalled compiz. Now my window manger doesn't seem to be working. Firefox has no top bar so I can move or minimize it, and when I press the 'show desktop' button in the corner is says I'm not running any window manager.  

Any ideas? Reading similar threads didn't help, but I did type in 'gnome-session' and got this:


gnome-session[1909]: WARNING: Unable to determine session: Unable to lookup session information for process '1909'
GNOME_KEYRING_CONTROL=/tmp/keyring-wNcgt8
GNOME_KEYRING_PID=1923
GNOME_KEYRING_CONTROL=/tmp/keyring-wNcgt8
GNOME_KEYRING_CONTROL=/tmp/keyring-wNcgt8
SSH_AUTH_SOCK=/tmp/keyring-wNcgt8/ssh

** (gnome-settings-daemon:1926): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:1926): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

(polkit-gnome-authentication-agent-1:1938): polkit-gnome-1-WARNING **: Unable to determine the session we are in: Remote Exception invoking org.freedesktop.ConsoleKit.Manager.GetSessionForUnixProcess() on /org/freedesktop/ConsoleKit/Manager at name org.freedesktop.ConsoleKit: org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1938' org.freedesktop.ConsoleKit.Manager.GeneralError Unable%20to%20lookup%20session%20information%20for%20process%20%271938%27
Initializing nautilus-gdu extension
An instance of nm-applet is already running.

(gnome-power-manager:1945): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x88dbc78'

** (gnome-settings-daemon:1926): WARNING **: Grab failed for some keys, another application may already have access the them.

** (gnome-settings-daemon:1926): WARNING **: Clipboard manager is already running.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

** (gnome-screensaver:2028): WARNING **: screensaver already running in this session
Failure: Module initalization failed

** (gnome-user-share:2035): WARNING **: gnome-user-share cannot be started as root for security reasons.
evolution-alarm-notify-Message: Setting timeout for 55794 1278633600 1278577806
evolution-alarm-notify-Message:  Thu Jul  8 17:00:00 2010

evolution-alarm-notify-Message:  Thu Jul  8 01:30:06 2010

^CTraceback (most recent call last):
  File "/usr/share/system-config-printer/applet.py", line 433, in <module>
    waitloop.run()
KeyboardInterrupt
gnome-session[1909]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: WARNING: Client '(null)' failed to reply before timeout
gnome-session[1909]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: WARNING: Client '(null)' failed to reply before timeout
gnome-session[1909]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: WARNING: Client '(null)' failed to reply before timeout
gnome-session[1909]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[1909]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed

** (update-notifier:2067): WARNING **: not starting for system user

Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

(gnome-panel:2057): EggSMClient-WARNING **: Failed to connect to the session manager: IO error occured opening connection

cable@Progress:~$ GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Message did not receive a reply (timeout by message bus))
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2057): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name




Thank you.

---

### Post by aeiah on 2010-07-08
well i suppose this is what happens when you select compiz as your window manager, and then uninstall it...

you'll want to use metacity as your window manager, i presume. try running ```
metacity --replace
``` in a terminal whilst on your desktop and see what it does. if it works that may be all there is to it, or maybe you'll have to edit a gnome session file or startup command or something.

---

### Post by C4BL3 on 2010-07-08
nice. the command worked in restoring metacity, but when I restart my computer it's back to the way it was.   I guess I will have to edit a gnome session or startup command? How do I do this?

---

### Post by C4BL3 on 2010-07-08
> **aeiah said:**
> well i suppose this is what happens when you select compiz as your window manager, and then uninstall it...

you'll want to use metacity as your window manager, i presume. try running ```
metacity --replace
``` in a terminal whilst on your desktop and see what it does. if it works that may be all there is to it, or maybe you'll have to edit a gnome session file or startup command or something.

   How do I edit a gnome session file or startup command? I already downloaded the boot up manager, but doesn't seem to work.

---

