---
title: "notify-send running as &quot;mail&quot; user not working"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Guruprasad on 2010-12-07
I have a script that runs every five min as user mail.

In that script I want to use notify-send command.

But the script gives following errors

> libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified
Autolaunch error: X11 initialization failed.


** (notify-send:6440): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:6440): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:6440): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified
Autolaunch error: X11 initialization failed.


** (notify-send:6440): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:6440): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed
you have mail


If i run the script as current user it works.

---

