---
title: "X connection over SSH troubles (keyboard settings, nm-applet, crash on disconnect)"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by krandun on 2008-07-22
Hello.
 Thank you for taking the time to read this far.

I'm trying to set my Ubuntu box up for remote X connections over SSH, in case some sort of remote administration dilemma comes up that can only be solved (or can more easily be solved) using a GUI. So far, I have SSH working on a non-standard port using RSA PKE as the only authentication method. I'm logging in from a Windows XP machine, using PuTTY to make the SSH connection, and Xming as the remote display. At the moment, instead of forwarding individual X application windows, I have PuTTY autorun "gnome-session &" on connect. This gives me the GNOME desktop in Xming.

I'm having 3 main problems with my current setup, and haven't been able to solve them on my own after a week of looking (both in UbuntuForums and on Google).
1. When I log in remotely as explained above, I get an error about the keyboard layout in X not matching the layout in GNOME.
```
The X system keyboard settings differ from your
 current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options,
 but the following settings were found: model "pc102",
 layout "en_US" and no options.

Which set would you like to use?
```
I select "Keep GNOME settings" every time.
If I keep logging in only using X forwarding over SSH, I don't get that error again. However, if I log in locally I have the same problem over again.

2. When I log in this way, nm-applet isn't shown in the systray. I don't care about that, I'm not going to mess with the networking settings while I'm remotely networked. What bothers me is that my PuTTY terminal scrolls this error the entire time I'm connected:
```
** (nm-applet:[PID here]): WARNING **: <WARN< nma_dbus_init(): could not acquire its 
service. dbus_bus_acquire_service() says: 'Connection ":1.69" is not allowed to
 own the service "org.freedesktop.NetworkManagerInfo" due to security policies 
in the configuration file'
```

3. If I try to log out from Xming, it starts to close everything out just fine, then hangs when it gets down to just my wallpaper and I get this in PuTTY terminal:
```
** (gnome-session:8233): WARNING **: Failed to authenticate with GDM

** (gnome-session:8233): WARNING **: Failed to authenticate with GDM
alarm-notify.c:274 (alarm_notify_finalize) - Finalize
 alarm-notify.c:259 (dequeue_client) - Removing client 0x80bae50
 alarm-queue.c:2169 (alarm_queue_remove_client) - Posting a task
alarm-queue.c:2118 (alarm_queue_remove_async)
alarm-queue.c:2090 (remove_client_alarms) - size 0
alarm-queue.c:2123 (alarm_queue_remove_async) - Disconnecting Client
alarm-queue.c:2132 (alarm_queue_remove_async) - Disconnecting Query
alarm-notify.c:259 (dequeue_client) - Removing client 0x809f880
 alarm-queue.c:2169 (alarm_queue_remove_client) - Posting a task
alarm-queue.c:2118 (alarm_queue_remove_async)
alarm-queue.c:2090 (remove_client_alarms) - size 0
alarm-queue.c:2123 (alarm_queue_remove_async) - Disconnecting Client
alarm-queue.c:2132 (alarm_queue_remove_async) - Disconnecting Query
alarm-notify.c:259 (dequeue_client) - Removing client 0x80bdc90
 alarm-queue.c:2169 (alarm_queue_remove_client) - Posting a task
alarm-queue.c:2118 (alarm_queue_remove_async)
alarm-queue.c:2090 (remove_client_alarms) - size 0
alarm-queue.c:2123 (alarm_queue_remove_async) - Disconnecting Client
alarm-queue.c:2132 (alarm_queue_remove_async) - Disconnecting Query
alarm-notify.c:259 (dequeue_client) - Removing client 0x80bae60
 alarm-queue.c:2169 (alarm_queue_remove_client) - Posting a task
alarm-queue.c:2118 (alarm_queue_remove_async)
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
alarm-queue.c:2090 (remove_client_alarms) - size 0
alarm-queue.c:2123 (alarm_queue_remove_async) - Disconnecting Client
alarm-queue.c:2132 (alarm_queue_remove_async) - Disconnecting Query
alarm-queue.c:1941 (alarm_queue_done)
```
I'm worried that shutting down this way might not be good, but how should I shut down? My current compromise is to log out, then terminate the PuTTY session.

Thank you again.
Krandun

---

