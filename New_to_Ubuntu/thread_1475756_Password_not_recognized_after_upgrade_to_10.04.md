---
title: "Password not recognized after upgrade to 10.04"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by dcahill on 2010-05-07
After upgrading to 10.04 I can´t log in normally. Ubuntu does not recocgnize my password. 

I can log in from a recovery mode command line so I tried resetting my password with the passwd commnad but the problem remains. 

Any help will be appreciated.

---

### Post by jd65pl on 2010-05-07
do you still have the same keyboard mapping as you did before the upgrade?

If your password contains special characters this may be the issue

---

### Post by dcahill on 2010-05-07
Not sure about keyboadr mapping but my password is very simple without special characters. 

The strange thing is that I can log in perfectly from the recovery command line and not from the default graphical login screen.

---

### Post by jd65pl on 2010-05-07
Do you have any gdm errors? From the recovery console

```
grep -iE gdm /var/log/syslog
```

---

### Post by dcahill on 2010-05-08
Yes a long list of errors scrolls by.

---

### Post by jd65pl on 2010-05-09
Are they all errors? Can you post the output? The command below will put the log output to a file called syslog.txt in your home directory for you to upload to here.

```
grep -iE gdm /var/log/syslog > ~/syslog.txt
```

---

### Post by jd65pl on 2010-05-09
It seems [others]("http://ubuntuforums.org/showthread.php?t=1465837&page=3") may be having similar issues, might be worth you taking a look. Can you still upload syslog, it will make pin pointing the issue easier.

---

### Post by dcahill on 2010-05-09
May  4 22:58:13 dcahill-laptop gdm-binary[3704]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  4 22:58:14 dcahill-laptop gdm-binary[3704]: WARNING: Unable to find users: no seat-id found
May  4 22:58:25 dcahill-laptop gdm-simple-greeter[3970]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  4 22:58:25 dcahill-laptop gdm-simple-greeter[3970]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  5 11:25:40 dcahill-laptop gdm-binary[3515]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 11:25:40 dcahill-laptop gdm-binary[3515]: WARNING: Unable to find users: no seat-id found
May  5 11:25:53 dcahill-laptop gdm-simple-greeter[3957]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 11:25:53 dcahill-laptop gdm-simple-greeter[3957]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  5 16:34:47 dcahill-laptop gdm-binary[3410]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 16:34:47 dcahill-laptop gdm-binary[3410]: WARNING: Unable to find users: no seat-id found
May  5 16:34:48 dcahill-laptop gdm-binary[3410]: WARNING: GdmDisplay: display lasted 1.256544 seconds
May  5 16:34:58 dcahill-laptop gdm-simple-greeter[3980]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 16:34:59 dcahill-laptop gdm-simple-greeter[3980]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  5 16:35:05 dcahill-laptop gdm-session-worker[3985]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 16:35:05 dcahill-laptop gdm-simple-greeter[3980]: WARNING: Default session is not available
May  5 16:35:13 dcahill-laptop gdm-session-worker[4131]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 16:35:18 dcahill-laptop gdm-simple-greeter[4225]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 16:35:18 dcahill-laptop gdm-simple-greeter[4225]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  5 16:35:31 dcahill-laptop gdm-session-worker[4229]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 16:35:31 dcahill-laptop gdm-simple-greeter[4225]: WARNING: Default session is not available
May  5 16:35:42 dcahill-laptop gdm-session-worker[4240]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 16:35:42 dcahill-laptop gdm-simple-greeter[4225]: WARNING: Default session is not available
May  5 16:35:45 dcahill-laptop gdm-simple-greeter[4225]: WARNING: Default session is not available
May  5 16:35:51 dcahill-laptop gdm-session-worker[4288]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 16:36:00 dcahill-laptop gdm-simple-greeter[4384]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 16:36:00 dcahill-laptop gdm-simple-greeter[4384]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  5 17:06:09 dcahill-laptop gdm-binary[3401]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 17:06:09 dcahill-laptop gdm-binary[3401]: WARNING: Unable to find users: no seat-id found
May  5 17:06:21 dcahill-laptop gdm-simple-greeter[3960]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 17:06:21 dcahill-laptop gdm-simple-greeter[3960]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  5 17:06:32 dcahill-laptop gdm-session-worker[3961]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 17:06:32 dcahill-laptop gdm-simple-greeter[3960]: WARNING: Default session is not available
May  5 17:06:37 dcahill-laptop gdm-session-worker[4102]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 17:06:43 dcahill-laptop gdm-simple-greeter[4195]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 17:06:43 dcahill-laptop gdm-simple-greeter[4195]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  5 17:07:02 dcahill-laptop gdm-session-worker[4199]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 17:07:02 dcahill-laptop gdm-simple-greeter[4195]: WARNING: Default session is not available
May  5 17:07:06 dcahill-laptop gdm-simple-greeter[4195]: WARNING: Default session is not available
May  5 17:07:11 dcahill-laptop gdm-session-worker[4253]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 17:07:17 dcahill-laptop gdm-simple-greeter[4347]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  5 17:07:17 dcahill-laptop gdm-simple-greeter[4347]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  5 17:07:57 dcahill-laptop gdm-session-worker[4348]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 17:07:57 dcahill-laptop gdm-simple-greeter[4347]: WARNING: Default session is not available
May  6 01:40:45 dcahill-laptop gdm-binary[3527]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 01:40:45 dcahill-laptop gdm-binary[3527]: WARNING: Unable to find users: no seat-id found
May  6 01:40:56 dcahill-laptop gdm-simple-greeter[3968]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 01:40:56 dcahill-laptop gdm-simple-greeter[3968]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 01:41:09 dcahill-laptop gdm-session-worker[3973]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 01:41:09 dcahill-laptop gdm-simple-greeter[3968]: WARNING: Default session is not available
May  6 01:41:33 dcahill-laptop gdm-session-worker[4110]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 01:41:40 dcahill-laptop gdm-simple-greeter[4203]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 01:41:40 dcahill-laptop gdm-simple-greeter[4203]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 01:42:02 dcahill-laptop gdm-session-worker[4206]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 01:42:02 dcahill-laptop gdm-simple-greeter[4203]: WARNING: Default session is not available
May  6 01:42:19 dcahill-laptop gdm-session-worker[4240]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 01:42:19 dcahill-laptop gdm-simple-greeter[4203]: WARNING: Default session is not available
May  6 01:42:31 dcahill-laptop gdm-session-worker[4244]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 01:42:31 dcahill-laptop gdm-simple-greeter[4203]: WARNING: Default session is not available
May  6 01:51:34 dcahill-laptop kernel: [   31.325401] type=1505 audit(1273121494.912:5):  operation="profile_load" pid=828 name="/usr/share/gdm/guest-session/Xsession"
May  6 01:51:37 dcahill-laptop gdm-binary[1049]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 01:51:37 dcahill-laptop gdm-binary[1049]: WARNING: Unable to find users: no seat-id found
May  6 01:51:48 dcahill-laptop gdm-simple-greeter[1520]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 01:51:48 dcahill-laptop gdm-simple-greeter[1520]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 01:51:51 dcahill-laptop gdm-session-worker[1536]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 01:51:51 dcahill-laptop gdm-simple-greeter[1520]: WARNING: Default session is not available
May  6 01:51:55 dcahill-laptop gdm-session-worker[1673]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 01:51:55 dcahill-laptop kernel: [   52.319934] type=1503 audit(1273121515.902:17):  operation="open" pid=1673 parent=1536 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  6 01:52:01 dcahill-laptop gdm-simple-greeter[1769]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 01:52:01 dcahill-laptop gdm-simple-greeter[1769]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 01:52:07 dcahill-laptop gdm-session-worker[1772]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 01:52:07 dcahill-laptop gdm-simple-greeter[1769]: WARNING: Default session is not available
May  6 07:44:32 dcahill-laptop kernel: [   30.094957] type=1505 audit(1273142672.702:5):  operation="profile_load" pid=808 name="/usr/share/gdm/guest-session/Xsession"
May  6 07:44:34 dcahill-laptop gdm-binary[889]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 07:44:34 dcahill-laptop gdm-binary[889]: WARNING: Unable to find users: no seat-id found
May  6 07:44:43 dcahill-laptop gdm-simple-greeter[1442]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 07:44:43 dcahill-laptop gdm-simple-greeter[1442]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 09:35:50 dcahill-laptop kernel: [   29.813337] type=1505 audit(1273149350.289:5):  operation="profile_load" pid=777 name="/usr/share/gdm/guest-session/Xsession"
May  6 09:35:52 dcahill-laptop gdm-binary[862]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 09:35:52 dcahill-laptop gdm-binary[862]: WARNING: Unable to find users: no seat-id found
May  6 09:36:02 dcahill-laptop gdm-simple-greeter[1482]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 09:36:02 dcahill-laptop gdm-simple-greeter[1482]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 09:36:05 dcahill-laptop gdm-session-worker[1492]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 09:36:05 dcahill-laptop gdm-simple-greeter[1482]: WARNING: Default session is not available
May  6 09:36:10 dcahill-laptop gdm-session-worker[1645]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 09:36:10 dcahill-laptop kernel: [   50.130230] type=1503 audit(1273149370.609:17):  operation="open" pid=1645 parent=1492 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  6 09:36:16 dcahill-laptop gdm-simple-greeter[1740]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 09:36:16 dcahill-laptop gdm-simple-greeter[1740]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 09:36:17 dcahill-laptop gdm-session-worker[1744]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 09:36:17 dcahill-laptop gdm-simple-greeter[1740]: WARNING: Default session is not available
May  6 09:36:26 dcahill-laptop gdm-session-worker[1754]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 09:36:26 dcahill-laptop gdm-simple-greeter[1740]: WARNING: Default session is not available
May  6 09:36:34 dcahill-laptop gdm-session-worker[1758]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 09:36:34 dcahill-laptop gdm-simple-greeter[1740]: WARNING: Default session is not available
May  6 09:36:46 dcahill-laptop gdm-session-worker[1764]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 09:36:46 dcahill-laptop gdm-simple-greeter[1740]: WARNING: Default session is not available
May  6 09:38:21 dcahill-laptop kernel: [   29.875624] type=1505 audit(1273149501.233:5):  operation="profile_load" pid=848 name="/usr/share/gdm/guest-session/Xsession"
May  6 17:14:44 dcahill-laptop kernel: [   30.914803] type=1505 audit(1273176884.524:5):  operation="profile_load" pid=830 name="/usr/share/gdm/guest-session/Xsession"
May  6 17:14:45 dcahill-laptop gdm-binary[884]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 17:14:46 dcahill-laptop gdm-binary[884]: WARNING: Unable to find users: no seat-id found
May  6 17:14:56 dcahill-laptop gdm-simple-greeter[1368]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 17:14:57 dcahill-laptop gdm-simple-greeter[1368]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 17:15:02 dcahill-laptop gdm-session-worker[1371]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 17:15:03 dcahill-laptop gdm-simple-greeter[1368]: WARNING: Default session is not available
May  6 17:15:09 dcahill-laptop gdm-session-worker[1605]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 17:15:09 dcahill-laptop kernel: [   56.165917] type=1503 audit(1273176909.774:17):  operation="open" pid=1605 parent=1371 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  6 17:15:15 dcahill-laptop gdm-simple-greeter[1701]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  6 17:15:15 dcahill-laptop gdm-simple-greeter[1701]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  6 17:15:24 dcahill-laptop gdm-session-worker[1705]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 17:15:24 dcahill-laptop gdm-simple-greeter[1701]: WARNING: Default session is not available
May  6 17:15:35 dcahill-laptop gdm-session-worker[1714]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 17:15:35 dcahill-laptop gdm-simple-greeter[1701]: WARNING: Default session is not available
May  6 17:15:47 dcahill-laptop gdm-session-worker[1722]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  6 17:15:47 dcahill-laptop gdm-simple-greeter[1701]: WARNING: Default session is not available
May  7 12:00:59 dcahill-laptop kernel: [   30.996720] type=1505 audit(1273244459.352:11):  operation="profile_load" pid=812 name="/usr/share/gdm/guest-session/Xsession"
May  7 12:03:01 dcahill-laptop kernel: [   29.651270] type=1505 audit(1273244581.253:5):  operation="profile_load" pid=837 name="/usr/share/gdm/guest-session/Xsession"
May  7 12:03:03 dcahill-laptop gdm-binary[1016]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  7 12:03:04 dcahill-laptop gdm-binary[1016]: WARNING: Unable to find users: no seat-id found
May  7 12:03:12 dcahill-laptop gdm-simple-greeter[1508]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  7 12:03:12 dcahill-laptop gdm-simple-greeter[1508]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  7 12:03:16 dcahill-laptop gdm-session-worker[1511]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  7 12:03:16 dcahill-laptop gdm-simple-greeter[1508]: WARNING: Default session is not available
May  7 12:03:23 dcahill-laptop gdm-session-worker[1645]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  7 12:03:23 dcahill-laptop kernel: [   51.935082] type=1503 audit(1273244603.533:17):  operation="open" pid=1645 parent=1511 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  7 12:03:29 dcahill-laptop gdm-simple-greeter[1739]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  7 12:03:29 dcahill-laptop gdm-simple-greeter[1739]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  7 12:03:33 dcahill-laptop gdm-session-worker[1742]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  7 12:03:33 dcahill-laptop gdm-simple-greeter[1739]: WARNING: Default session is not available
May  7 13:58:59 dcahill-laptop kernel: [   30.340084] type=1505 audit(1273251539.708:5):  operation="profile_load" pid=846 name="/usr/share/gdm/guest-session/Xsession"
May  8 07:59:02 dcahill-laptop kernel: [   30.774882] type=1505 audit(1273316342.130:5):  operation="profile_load" pid=776 name="/usr/share/gdm/guest-session/Xsession"
May  8 23:55:29 dcahill-laptop kernel: [   30.491907] type=1505 audit(1273373729.849:5):  operation="profile_load" pid=846 name="/usr/share/gdm/guest-session/Xsession"
May  9 00:00:11 dcahill-laptop kernel: [   29.747064] type=1505 audit(1273374011.351:5):  operation="profile_load" pid=773 name="/usr/share/gdm/guest-session/Xsession"
May  9 00:00:13 dcahill-laptop gdm-binary[911]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:00:13 dcahill-laptop gdm-binary[911]: WARNING: Unable to find users: no seat-id found
May  9 00:00:23 dcahill-laptop gdm-simple-greeter[1451]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:00:23 dcahill-laptop gdm-simple-greeter[1451]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 00:24:43 dcahill-laptop kernel: [   29.891707] type=1505 audit(1273375483.506:5):  operation="profile_load" pid=866 name="/usr/share/gdm/guest-session/Xsession"
May  9 00:24:44 dcahill-laptop gdm-binary[985]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:24:45 dcahill-laptop gdm-binary[985]: WARNING: Unable to find users: no seat-id found
May  9 00:24:56 dcahill-laptop gdm-simple-greeter[1562]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:24:56 dcahill-laptop gdm-simple-greeter[1562]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 00:24:58 dcahill-laptop gdm-session-worker[1566]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  9 00:24:58 dcahill-laptop gdm-simple-greeter[1562]: WARNING: Default session is not available
May  9 00:25:17 dcahill-laptop gdm-session-worker[1727]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:25:17 dcahill-laptop kernel: [   64.348006] type=1503 audit(1273375517.956:17):  operation="open" pid=1727 parent=1566 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  9 00:25:23 dcahill-laptop gdm-simple-greeter[1821]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:25:23 dcahill-laptop gdm-simple-greeter[1821]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 00:25:27 dcahill-laptop gdm-session-worker[1824]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  9 00:25:27 dcahill-laptop gdm-simple-greeter[1821]: WARNING: Default session is not available
May  9 00:25:31 dcahill-laptop gdm-session-worker[1877]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:25:31 dcahill-laptop kernel: [   77.993191] type=1503 audit(1273375531.606:18):  operation="open" pid=1877 parent=1824 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  9 00:25:37 dcahill-laptop gdm-simple-greeter[1972]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:25:37 dcahill-laptop gdm-simple-greeter[1972]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 00:25:40 dcahill-laptop gdm-session-worker[1975]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  9 00:25:40 dcahill-laptop gdm-simple-greeter[1972]: WARNING: Default session is not available
May  9 00:25:47 dcahill-laptop gdm-simple-greeter[1972]: WARNING: Mapping failed for /usr/lib/locale/locale-archive: Failed to open file '/usr/lib/locale/locale-archive': open() failed: No such file or directory
May  9 00:26:16 dcahill-laptop gdm-session-worker[2035]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:26:17 dcahill-laptop kernel: [  123.416973] type=1503 audit(1273375577.026:19):  operation="open" pid=2035 parent=1975 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  9 00:26:23 dcahill-laptop gdm-simple-greeter[2130]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:26:23 dcahill-laptop gdm-simple-greeter[2130]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 00:26:27 dcahill-laptop gdm-session-worker[2133]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  9 00:26:27 dcahill-laptop gdm-simple-greeter[2130]: WARNING: Default session is not available
May  9 00:26:52 dcahill-laptop gdm-session-worker[2192]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:26:52 dcahill-laptop kernel: [  159.043382] type=1503 audit(1273375612.656:20):  operation="open" pid=2192 parent=2133 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  9 00:26:59 dcahill-laptop gdm-simple-greeter[2287]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:26:59 dcahill-laptop gdm-simple-greeter[2287]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 00:57:16 dcahill-laptop kernel: [   30.847064] type=1505 audit(1273377436.212:5):  operation="profile_load" pid=823 name="/usr/share/gdm/guest-session/Xsession"
May  9 00:57:49 dcahill-laptop gdm-binary[1115]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:57:49 dcahill-laptop gdm-binary[1115]: WARNING: Unable to find users: no seat-id found
May  9 00:57:56 dcahill-laptop gdm-simple-greeter[1224]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:57:56 dcahill-laptop gdm-simple-greeter[1224]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 00:57:59 dcahill-laptop gdm-session-worker[1227]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  9 00:57:59 dcahill-laptop gdm-simple-greeter[1224]: WARNING: Default session is not available
May  9 00:58:04 dcahill-laptop gdm-session-worker[1363]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:58:04 dcahill-laptop kernel: [   79.299867] type=1503 audit(1273377484.662:17):  operation="open" pid=1363 parent=1227 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/dcahill/.profile"
May  9 00:58:10 dcahill-laptop gdm-simple-greeter[1458]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 00:58:10 dcahill-laptop gdm-simple-greeter[1458]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 00:58:35 dcahill-laptop gdm-session-worker[1461]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  9 00:58:35 dcahill-laptop gdm-simple-greeter[1458]: WARNING: Default session is not available
May  9 00:58:55 dcahill-laptop gdm-session-worker[1471]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  9 00:58:55 dcahill-laptop gdm-simple-greeter[1458]: WARNING: Default session is not available
May  9 21:00:56 dcahill-laptop kernel: [   29.770462] type=1505 audit(1273449656.128:5):  operation="profile_load" pid=869 name="/usr/share/gdm/guest-session/Xsession"
May  9 23:39:54 dcahill-laptop gdm-binary[1220]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 23:39:54 dcahill-laptop gdm-binary[1220]: WARNING: Unable to find users: no seat-id found
May  9 23:40:00 dcahill-laptop gdm-simple-greeter[1337]: GVFS-RemoteVolumeMonitor-WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory
May  9 23:40:01 dcahill-laptop gdm-simple-greeter[1337]: Gtk-WARNING: /build/buildd/gtk+2.0-2.19.7/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  9 23:58:11 dcahill-laptop kernel: [   30.295699] type=1505 audit(1273460291.652:8):  operation="profile_load" pid=840 name="/usr/share/gdm/guest-session/Xsession"

---

### Post by ranch hand on 2010-05-09
Hmm, interesting.  Do you have a remote desktop you are using?  Do you maybe have a second monitor that is confusing things here?

---

### Post by jd65pl on 2010-05-10
```
apt-get install gvfs-backends
```
Solves:
> WARNING: cannot open directory /usr/share/gvfs/remote-volume-monitors
(The above area does not relate to a monitor in the context of a display. It relates to virtual file systems mounted through fuse)

Do you have an NVidia gfx card?

---

### Post by ranch hand on 2010-05-10
> **jd65pl said:**
> ```
apt-get install gvfs-backends
```Solves:

(The above area does not relate to a monitor in the context of a display. It relates to virtual file systems mounted through fuse)

Do you have an NVidia gfx card?
Once again my ignorance is reduced a very little bit.  Thanks.

Should have known that from the mention of gvfs.  Sometimes I am hard of thinking.

---

### Post by dcahill on 2010-05-10
Thanks guys for takin the trouble to help me out!

More details:

I don´t have a remote desktop and the graphic card is an nVidia GeForce 7000. 
Laptop is Acer Aspire 7520-5626 AMD 64. 
Ubuntu is installed all on it´s own on a separate hard drive that I boot from. 
Problem started after an attempt to upgrade over the net. The logon screen was first blank and after trying to reconfigure is now very poor resolution. 
My only internet connection is with 3g modem using windows since it won´t run on Ubuntu.

Although I would prefer to learn how to fix this thing, is there a way to take a shortcut and re-install without loosing settings? They are not that critical anyway and I could even afford to loose them if it´s the only option.

---

### Post by jd65pl on 2010-05-11
Its possible that one of the settings is the thing causing the problem. However, you can copy your home directory to a new install to keep your user settings.

---

