---
title: "DVD, games, hibernation"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by bmacusa on 2010-05-22
I have been using Ubuntu on my desktop system since December, 2008 and have been exceedingly happy with it and have "converted" several other people.  However, since upgrading to 10.04, I have seen some problems...none of which existed until upgrading to Lucid.

My greatest concern is the fact that my DVD burner (TSST SH-S182D) will frequently not be recognized upon boot.  Even if it is recognized on boot, it will "drop off" within 5 - 10 minutes and I am unable to remount it.

Also (an incidental problem), many of the supplied games will not open. I get "loading Quadrapassel" for example, and then it simply stops.

Another issue is the fact that the systems shuts down when it should hibernate.  I believe I have solved this by disabling hibernation but it still is annoying to have to do this.

Is there a method of repairing this installation without having to re-install?

Thank you.

---

### Post by QLee on 2010-05-22
[QUOTE=bmacusa]I have been using Ubuntu on my desktop system since December, 2008 and have been exceedingly happy with it and have "converted" several other people.  However, since upgrading to 10.04, I have seen some problems...none of which existed until upgrading to Lucid.

My greatest concern is the fact that my DVD burner (TSST SH-S182D) will frequently not be recognized upon boot.  Even if it is recognized on boot, it will "drop off" within 5 - 10 minutes and I am unable to remount it.

Also (an incidental problem), many of the supplied games will not open. I get "loading Quadrapassel" for example, and then it simply stops.[/QUOTE]


Are you certain that everything is upgraded, for example with Update Manager?

[QUOTE=bmacusa]Another issue is the fact that the systems shuts down when it should hibernate.  I believe I have solved this by disabling hibernation but it still is annoying to have to do this.
[/QUOTE]

Well, hibernate is supposed to shut the system down. It writes the contents of RAM to swap purportedly to be able to get back to the same situation, then shuts down the system to conserve power.

---

### Post by bmacusa on 2010-05-22
Sorry 'bout the  ignorance in questioning the hibernation.  I am self-flagellating as I write.  Evidently, I had hibernation disabled before upgrading to Lucid since the system didn't shut down completely in Karmic.

The problem in shutting down is that, when I do shut down, I have to turn off the power and push the power button to reset the computer.  If I don't, the re-started computer won't give me an internet connection using a WebStar cable modem.  I tried researching this also and just wound up "living with it".

I do an update daily (Update Manager), whether notified or not.  Just out of curiosity, I uninstalled the games which were showing the start-up problem and re-installed them.  Same situation.

---

### Post by lidex on 2010-05-23
What is the output when you run quadrapassel from a Terminal="Applications->Accessories->Terminal"
```
quadrapassel 
```

---

### Post by bmacusa on 2010-05-23
I get the error message "Segmentation fault"

---

### Post by lidex on 2010-05-23
> **bmacusa said:**
> I get the error message "Segmentation fault"

No help there. Are you running lucid in a VM?

Can you:
```
cat ~/.xsession-errors
```

---

### Post by bmacusa on 2010-05-24
By VM I take it you mean Virtual Machine and the answer is no.  Lucid is the sole installation on a desktop PC.

When running the code you suggested, I get the following:
bruce@Bruce-desktop:~$ cat ~/.xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-zrKMoP
GNOME_KEYRING_PID=1678
GNOME_KEYRING_CONTROL=/tmp/keyring-zrKMoP
SSH_AUTH_SOCK=/tmp/keyring-zrKMoP/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-zrKMoP
SSH_AUTH_SOCK=/tmp/keyring-zrKMoP/ssh
Window manager warning: Failed to read saved session file /home/bruce/.config/metacity/sessions/10737ec61dd8325692127474684554337600000013420034.ms: Failed to open file '/home/bruce/.config/metacity/sessions/10737ec61dd8325692127474684554337600000013420034.ms': No such file or directory
gnome-session[1342]: WARNING: Could not launch application 'ubuntuone-client-applet.desktop': Unable to start application: Failed to execute child process "ubuntuone-client-applet" (No such file or directory)
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/bruce/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/bruce/.config/tracker/tracker.cfg'
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/bruce/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/bruce/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/bruce/.local/share/tracker/trackerd.log'

(polkit-gnome-authentication-agent-1:1715): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1715): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
17

(gnome-power-manager:1719): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8f31700'

** (gnome-power-manager:1719): WARNING **: Either HAL or DBUS are not working!

** (gnome-power-manager:1719): WARNING **: proxy failed

** (gnome-power-manager:1719): WARNING **: failed to get Computer root object

** (gnome-power-manager:1719): WARNING **: proxy NULL!!
Initializing nautilus-gdu extension
Unable to find a synaptics device.
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
Failure: Module initalization failed

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1932): Gdk-WARNING **: XID collision, trouble ahead
evolution-alarm-notify-Message: Setting timeout for 20324 1274767200 1274746876
evolution-alarm-notify-Message:  Tue May 25 00:00:00 2010

evolution-alarm-notify-Message:  Mon May 24 18:21:16 2010

** (update-notifier:2023): DEBUG: Skipping reboot required

(gnome-terminal:2080): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(gnome-terminal:2105): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

---

