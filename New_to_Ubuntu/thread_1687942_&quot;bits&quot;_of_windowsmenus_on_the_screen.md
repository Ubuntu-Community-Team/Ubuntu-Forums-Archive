---
title: "&quot;bits&quot; of windows/menus on the screen"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by Nico34 on 2011-02-14
Hi everyone,

my name is Nicola, I'm writing from Italy.


It happens randomly that when I open a menu in apps or in the top panel, "bits" of the current view remain stuck over the desktop or any other window.

For example, main menu with tracks of an icon movement:
[IMG]http://i51.tinypic.com/j7wb5v.jpg[/IMG]

Transmission over Firefox:
[IMG]http://i51.tinypic.com/34j563a.jpg[/IMG]

5 minutes ago it happened with an applet menu that came over Firefox search bar, keeping me from using it (or at least without seeing what I was writing in the blank).

As randomly as it appears it also disappears and I haven't yet figured out how; it can be after a couple of minutes or only with a restart.


Did someone ever experience this? How can it be fixed?

I have an ATI Radeon HD4550 with updated drivers.


Thanks in advance for your help :D

---

### Post by robsoles on 2011-02-14
Welcome to UF Nicola.

Not enough clues for me to try to help you solve that right away and chances are you could provide me clues till the cows came home and I still wouldn't see the problem to fix **BUT** that doesn't mean more clues won't enable others to help you much easier.

Please tell us:

Motherboard make & model?
Ubuntu flavour and version (which ISO did you install?)
Exactly what drivers you have selected (and updated) for the ATI Radeon HD4550? (Did 'Hardware Drivers' download and install the drivers? Did you get drivers from a website? Are the drivers from a repository via apt?)

---

### Post by matt_symes on 2011-02-14
Hi 

Welcome to the forums. Are you running Compiz ?

Kind regards

---

### Post by Nico34 on 2011-02-15
Thanks for your welcome :D

> **robsoles said:**
> Welcome to UF Nicola
Motherboard make & model?
Ubuntu flavour and version (which ISO did you install?)
Exactly what drivers you have selected (and updated) for the ATI Radeon HD4550? (Did 'Hardware Drivers' download and install the drivers? Did you get drivers from a website? Are the drivers from a repository via apt?)
I have an Asus P5G41C-M LX with an Intel Celeron E3300 on.
Ubuntu 10.10 (ubuntu-10.10-desktop-i386 ISO, downloaded from the official site)
I installed the fglrx drivers with the "Additional Drivers" tool

> **matt_symes said:**
> Hi 
Welcome to the forums. Are you running Compiz ?
Ehm... I don't know actually (and that's the part where you see I am a total noob :D)
I have Compiz installed with ccsm, but also Ubuntu Tweak that I use to enable Compositing needed for Docky.
I guess that's where I'm missing something :rolleyes:

---

### Post by matt_symes on 2011-02-15
Hi

First thing i would do is turn off Compiz and see if you still get the same problem. You will lose docky for a while but if it doesn't happen any more you can surmise it's something to do with compiz.

Are there any errors in your log files ~/.xsession-errors or /var/log/Xorg.0.log just after it happens ?

Another thing you could try is to roll back to the open source ATI driver and see if you still get the issue as well.

Kind regards

---

### Post by Nico34 on 2011-02-15
Thanks for the tip,

I think I'll uninstall Compiz, or is there a way to turn it off without uninstalling?

---

### Post by migs73 on 2011-02-15
I have had the same issue ([http://ubuntuforums.org/showthread.php?t=1681159](http://ubuntuforums.org/showthread.php?t=1681159)) but no help as yet.

I don't use compiz (I did do and removed it when the problem started). It would be nice if someone had an idea of what was causing it. I'll look into my logs next time it happens.

Running 10.10 PAE on a Dell inspiron 1501 with no propriety graphics drivers.

:(

---

### Post by Nico34 on 2011-02-15
Hi again,

uninstalled Compiz and rebooted but nothing has changed.

Many thanks to migs73 for his comment; I hadn't clearly noticed that this issue happens only with pop-up menus.

> **matt_symes said:**
> Are there any errors in your log files  ~/.xsession-errors or /var/log/Xorg.0.log just after it happens  ?
I tried this command in Terminal but it didn't work; can you please be more specific about the way to look at error logs?


[EDIT]: I have also uninstalled Docky and disabled Metacity Compositing from Ubuntu Tweak menu; I'm not quite sure but menus seem to be faster and smoother than before and the issue we're having has not yet happened.
I'll let you know.

---

### Post by robsoles on 2011-02-15
> **Nico34 said:**
> ...

I tried this command in Terminal but it didn't work; can you please be more specific about the way to look at error logs?


...

```
cat ~/.xsession-errors
cat /var/log/Xorg.0.log
```

There is a GUI log viewer as well, am trapped on Windows workstation right now so can't immediately check which menu, sorry.

'tail' is a command that can be used on the logs to either see the last 20 lines or you can 'follow' the log in terminal using '-f' switch```
tail -f /var/log/Xorg.0.log
```(Press [CTRL]+[C] to release the terminal).

---

### Post by matt_symes on 2011-02-16
Hi

Nico34 are you using 10.10 ? I noticed sdowney in the other thread was using a non proprietary nVidea driver. You were using a proprietary ATI driver. What are you using robsoles ?

As they are all different cards and drivers and the problem appears with both compiz installed and uninstalled that would lead me to think it might not be the graphics driver or compiz but you guys may want to see if there is a common denominator in your setup.

Kind regards

---

### Post by robsoles on 2011-02-16
Hey matt, I am on an NVIDIA "GeForce GTS 250" 1Gb 12+ months old using the current recommended proprietary drivers, I push a dual display setup using one decent monitor (1920x1080xy24") and one less decent (1600x1200xy19"), both at their full resolution as seperated desktops. Fairly vanilla install of Ubuntu 10.04, compiz doing 'extra' visual effects, wobbly windows, spinning cube and couple o'tothers and conky and pretty sure I haven't messed with metacity.

I have to report that it's been flawless for me from day dot, I do mean that the video functionality of the machine is excellent, I've tested the GPU by running several movies on both displays and starting a nice game and it greyed one or two of the movies whilst starting the game up and then all the video 'flowed evenly', the GPU fan came on pretty hard and perceptibly backed off for each item I closed :roll:

I can recommend my laptop too, Samsung NP-N150 works out of the box with Ubuntu recognising wifi, bluetooth etc from 10.04 onward with same lack of glitching in display, albeit not quite as capable of course.

---

### Post by Nico34 on 2011-02-16
> **matt_symes said:**
> Hi
Nico34 are you using 10.10 ?
Yes I'm on 10.10, fully updated

> **Nico34 said:**
> 
1) uninstalled Compiz and rebooted but nothing has changed.
2)I have also uninstalled Docky and disabled Metacity Compositing from Ubuntu Tweak menu; I'm not quite sure but menus seem to be faster and smoother than before and the issue we're having has not yet happened.
3)I have installed AWN and so enabled Metacity compositing; now the  funny thing is that the issue occurred again, but with a weaker effect  than before and above all it stayed in the "range" of the application:  for example in Shotwell the menus messed up but they didn't remain on  the screen when I closed the app.

So I guess it has something to do with compositing; could it be?

---

### Post by migs73 on 2011-02-16
Here is the output from this code
```
cat ~/.xsession-errors
cat /var/log/Xorg.0.log
```

This was during an episode as seen below.

```
/home/mike/.gtkrc-2.0:8: Unable to find include file: ".themes/nautilus/nautilus.rc"
`menu_proxy_module_load': gnome-system-monitor: undefined symbol: menu_proxy_module_load

(gnome-system-monitor:963): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-monitor: undefined symbol: menu_proxy_module_load

(gnome-system-monitor:963): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-monitor: undefined symbol: menu_proxy_module_load

(gnome-system-monitor:963): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-monitor: undefined symbol: menu_proxy_module_load

(gnome-system-monitor:963): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-monitor: undefined symbol: menu_proxy_module_load

(gnome-system-monitor:963): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-monitor: undefined symbol: menu_proxy_module_load

(gnome-system-monitor:963): Gtk-WARNING **: Failed to load type module: (null)


** (gnome-system-monitor:963): WARNING **: SELinux was found but is not enabled.

/home/mike/.gtkrc-2.0:8: Unable to find include file: ".themes/nautilus/nautilus.rc"
`menu_proxy_module_load': gnome-system-log: undefined symbol: menu_proxy_module_load

(gnome-system-log:2300): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-log: undefined symbol: menu_proxy_module_load

(gnome-system-log:2300): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-log: undefined symbol: menu_proxy_module_load

(gnome-system-log:2300): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-log: undefined symbol: menu_proxy_module_load

(gnome-system-log:2300): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-log: undefined symbol: menu_proxy_module_load

(gnome-system-log:2300): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-log: undefined symbol: menu_proxy_module_load

(gnome-system-log:2300): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-system-log: undefined symbol: menu_proxy_module_load

(gnome-system-log:2300): Gtk-WARNING **: Failed to load type module: (null)


(gnome-system-log:2300): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
/home/mike/.gtkrc-2.0:8: Unable to find include file: ".themes/nautilus/nautilus.rc"
`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:19710): Gtk-WARNING **: Failed to load type module: (null)

```

```
[    29.419] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    29.419] (**) Dell WMI hotkeys: always reports core events
[    29.419] (**) Dell WMI hotkeys: Device: "/dev/input/event7"
[    29.419] (II) Dell WMI hotkeys: Found keys
[    29.419] (II) Dell WMI hotkeys: Configuring as keyboard
[    29.419] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    29.419] (**) Option "xkb_rules" "evdev"
[    29.419] (**) Option "xkb_model" "evdev"
[    29.419] (**) Option "xkb_layout" "gb"
[    29.928] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    29.928] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    29.929] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.929] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[    29.966] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    29.966] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    29.966] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.966] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[    30.005] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    30.005] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    30.005] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.005] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[    30.040] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    30.040] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    30.040] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.040] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[    50.834] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    50.834] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    50.834] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.834] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[    50.862] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    50.862] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    50.862] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.862] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[    50.887] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    50.887] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    50.887] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.887] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[    52.652] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    52.652] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    52.652] (II) RADEON(0): Printing DDC gathered Modelines:
[    52.652] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[    57.168] (II) RADEON(0): EDID vendor "LPL", prod id 43264
[    57.168] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    57.168] (II) RADEON(0): Printing DDC gathered Modelines:
[    57.168] (II) RADEON(0): Modeline "1280x800"x0.0   72.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (50.2 kHz)
[  1156.861] (II) XKB: reuse xkmfile /var/lib/xkb/server-EF269B69E2D18D6A561ED7A916EAB18CA529C22A.xkm

```

Hope this helps, if not I might raise a bug in Launchpag

---

### Post by Nico34 on 2011-02-16
Well, I thought I had partially solved but it happened again.

Here is what I get from:
```
cat ~/.xsession-errors
cat /var/log/Xorg.0.lo
``````
nico@ubuntu:~$ cat ~/.xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=it_IT.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
_IceTransmkdir: ERROR: euid != 0,directory /tmp/.ICE-unix will not be created.
GNOME_KEYRING_CONTROL=/tmp/keyring-tIR1Bo
GNOME_KEYRING_PID=1182
GNOME_KEYRING_CONTROL=/tmp/keyring-tIR1Bo
gnome-session[1131]: WARNING: Could not launch application 'docky.desktop': Unable to start application: Esecuzione del processo figlio "docky" non riuscita (File o directory non esistente)

(polkit-gnome-authentication-agent-1:1291): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1291): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1287): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1287): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension
** Message: applet now embedded in the notification area

(nautilus:1284): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Unable to find a synaptics device.
Screen is composited
** (avant-window-navigator:1285): DEBUG: Updating dialog colours
** (avant-window-navigator:1285): DEBUG: Spawned awn-applet[1383] for "taskmanager.desktop", UID: 1297810058, XID: 25165868
** (avant-window-navigator:1285): DEBUG: Spawned awn-applet[1385] for "file-browser-launcher.desktop", UID: 1297860289, XID: 25165869
** (avant-window-navigator:1285): DEBUG: Spawned awn-applet[1386] for "weather.desktop", UID: 1297809748, XID: 25165870
** (avant-window-navigator:1285): DEBUG: Spawned awn-applet[1387] for "mail.desktop", UID: 1297809828, XID: 25165871
** (avant-window-navigator:1285): DEBUG: Spawned awn-applet[1388] for "indicator-applet.desktop", UID: 1297860343, XID: 25165872
** (avant-window-navigator:1285): DEBUG: Spawned awn-applet[1389] for "cairo-clock.desktop", UID: 1297860178, XID: 25165873

(awn-applet:1388): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.me on /org/ayatana/indicator/me/menu: Could not get owner of name 'org.ayatana.indicator.me': no such name

(awn-applet:1388): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.session on /org/ayatana/indicator/session/menu: Could not get owner of name 'org.ayatana.indicator.session': no such name
(awn-applet:1388): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(awn-applet:1388): Indicator-Application-DEBUG: Setup proxy signals
(awn-applet:1388): Indicator-Application-DEBUG: Connect to them.
(awn-applet:1388): Indicator-Application-DEBUG: Request current apps
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)

(awn-applet:1388): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_property_get_value: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(awn-applet:1388): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_property_get_value: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(awn-applet:1388): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_property_get_value: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(awn-applet:1388): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_property_get_value: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(awn-applet:1388): GLib-CRITICAL **: g_string_overwrite: assertion `val != NULL' failed

(awn-applet:1388): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed
** (awn-applet:1388): DEBUG: new_application_item ("Chat")
** (awn-applet:1388): DEBUG: new_application_item ("Email")
** (awn-applet:1388): DEBUG: new_application_item ("Componi nuovo messaggio")
** (awn-applet:1388): DEBUG: new_application_item ("Contatti")
** (awn-applet:1388): DEBUG: new_application_item ("Social network")

(awn-applet:1388): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed

(awn-applet:1388): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed

(awn-applet:1388): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed

(awn-applet:1388): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed
** (awn-applet:1388): DEBUG: Using user icon for 'Sessione ospite' from file: (null)
** (awn-applet:1388): DEBUG: entry hint: Pubblica messaggio...
** (awn-applet:1388): DEBUG: entry_maybe_show_hint, nothing in the entry or not focused, so setting the hint to: Pubblica messaggio...

(awn-applet:1388): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.26.0/gobject/gsignal.c:2275: signal `destroy' is invalid for instance `0x819ddb0'

** (gnome-settings-daemon:1186): WARNING **: Got less number of items in credentials hash table than expected!
** (nm-applet:1287): DEBUG: foo_client_state_changed_cb
** (nm-applet:1287): DEBUG: foo_client_state_changed_cb
** (awn-applet:1388): DEBUG: entry hint: Pubblica su: facebook...
** (awn-applet:1388): DEBUG: entry hint: Pubblica su: facebook...
** (awn-applet:1388): DEBUG: new_application_item ("(null)")
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** (avant-window-navigator:1285): DEBUG: Updating dialog colours
** (update-notifier:1684): DEBUG: aptdaemon on bus: 0
** (update-notifier:1684): DEBUG: Skipping reboot required
** (avant-window-navigator:1285): DEBUG: Updating dialog colours

(gnome-appearance-properties:1692): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1692): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
** (avant-window-navigator:1285): DEBUG: Updating dialog colours

(nautilus:1284): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
** (avant-window-navigator:1285): DEBUG: Updating dialog colours
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** (avant-window-navigator:1285): DEBUG: Updating dialog colours
** (avant-window-navigator:1285): DEBUG: Updating dialog colours
** (avant-window-navigator:1285): DEBUG: Updating dialog colours
** (avant-window-navigator:1285): DEBUG: Updating dialog colours

** (gnome-screensaver:1554): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_application_handlers

** (gnome-screensaver:1554): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_command_line

** (gnome-screensaver:1554): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_printing

** (gnome-screensaver:1554): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_print_setup

** (gnome-screensaver:1554): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_save_to_disk
** (awn-applet:1388): DEBUG: new_application_item ("(null)")
Avviso del window manager: Received a _NET_WM_MOVERESIZE message for 0x440003c (In arrivo ); these messages lack timestamps and therefore suck.
NOTE: child process received `Goodbye', closing down

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:1892): Gdk-WARNING **: XID collision, trouble ahead
Avviso del window manager: Received a _NET_WM_MOVERESIZE message for 0x4c00004 (nico@ubunt); these messages lack timestamps and therefore suck.

``````
nico@ubuntu:~$ cat /var/log/Xorg.0.log
[    19.232] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    19.232] X Protocol Version 11, Revision 0
[    19.232] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    19.232] Current Operating System: Linux ubuntu 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    19.232] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-25-generic root=UUID=d0fd67c8-e5c5-4297-8432-9b7dd24b21ac ro quiet splash
[    19.232] Build Date: 09 January 2011  12:14:58PM
[    19.232] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    19.232] Current version of pixman: 0.18.4
[    19.232]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.232] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.232] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 16 18:56:39 2011
[    19.232] (==) Using config file: "/etc/X11/xorg.conf"
[    19.232] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.232] (==) No Layout section.  Using the first Screen section.
[    19.232] (**) |-->Screen "Default Screen" (0)
[    19.232] (**) |   |-->Monitor "<default monitor>"
[    19.232] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    19.232] (**) |   |-->Device "Default Device"
[    19.232] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    19.233] (==) Automatically adding devices
[    19.233] (==) Automatically enabling devices
[    19.233] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.233]     Entry deleted from font path.
[    19.233] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    19.233] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.233] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.233] (II) Loader magic: 0x81f9b00
[    19.233] (II) Module ABI versions:
[    19.233]     X.Org ANSI C Emulation: 0.4
[    19.233]     X.Org Video Driver: 8.0
[    19.233]     X.Org XInput driver : 11.0
[    19.233]     X.Org Server Extension : 4.0
[    19.234] (--) PCI:*(0:1:0:0) 1002:9540:1458:21ae rev 0, Mem @ 0xe0000000/268435456, 0xfeae0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    19.234] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    19.234] (II) "extmod" will be loaded by default.
[    19.234] (II) "dbe" will be loaded by default.
[    19.234] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    19.234] (II) "record" will be loaded by default.
[    19.234] (II) "dri" will be loaded by default.
[    19.234] (II) "dri2" will be loaded by default.
[    19.234] (II) LoadModule: "glx"
[    19.234] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    19.234] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    19.234]     compiled for 7.6.0, module version = 1.0.0
[    19.234] (II) Loading extension GLX
[    19.234] (II) LoadModule: "extmod"
[    19.235] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.235] (II) Module extmod: vendor="X.Org Foundation"
[    19.235]     compiled for 1.9.0, module version = 1.0.0
[    19.235]     Module class: X.Org Server Extension
[    19.235]     ABI class: X.Org Server Extension, version 4.0
[    19.235] (II) Loading extension MIT-SCREEN-SAVER
[    19.235] (II) Loading extension XFree86-VidModeExtension
[    19.235] (II) Loading extension XFree86-DGA
[    19.235] (II) Loading extension DPMS
[    19.235] (II) Loading extension XVideo
[    19.235] (II) Loading extension XVideo-MotionCompensation
[    19.235] (II) Loading extension X-Resource
[    19.235] (II) LoadModule: "dbe"
[    19.235] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.235] (II) Module dbe: vendor="X.Org Foundation"
[    19.235]     compiled for 1.9.0, module version = 1.0.0
[    19.235]     Module class: X.Org Server Extension
[    19.235]     ABI class: X.Org Server Extension, version 4.0
[    19.235] (II) Loading extension DOUBLE-BUFFER
[    19.235] (II) LoadModule: "record"
[    19.235] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.235] (II) Module record: vendor="X.Org Foundation"
[    19.235]     compiled for 1.9.0, module version = 1.13.0
[    19.236]     Module class: X.Org Server Extension
[    19.236]     ABI class: X.Org Server Extension, version 4.0
[    19.236] (II) Loading extension RECORD
[    19.236] (II) LoadModule: "dri"
[    19.236] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.236] (II) Module dri: vendor="X.Org Foundation"
[    19.236]     compiled for 1.9.0, module version = 1.0.0
[    19.236]     ABI class: X.Org Server Extension, version 4.0
[    19.236] (II) Loading extension XFree86-DRI
[    19.236] (II) LoadModule: "dri2"
[    19.236] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.236] (II) Module dri2: vendor="X.Org Foundation"
[    19.236]     compiled for 1.9.0, module version = 1.2.0
[    19.236]     ABI class: X.Org Server Extension, version 4.0
[    19.236] (II) Loading extension DRI2
[    19.236] (II) LoadModule: "fglrx"
[    19.236] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    19.251] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    19.251]     compiled for 1.4.99.906, module version = 8.78.30
[    19.251]     Module class: X.Org Video Driver
[    19.252] (II) Loading sub module "fglrxdrm"
[    19.252] (II) LoadModule: "fglrxdrm"
[    19.252] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    19.252] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    19.252]     compiled for 1.8.99.905, module version = 8.78.30
[    19.252] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    19.252] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    19.252] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:30:49
[    19.252] (++) using VT number 7

[    19.253] (WW) Falling back to old probe method for fglrx
[    19.258] (II) Loading PCS database from /etc/ati/amdpcsdb
[    19.258] (--) Assigning device section with no busID to primary device
[    19.258] (--) Chipset Supported AMD Graphics Processor (0x9540) found
[    19.258] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    19.259] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    19.259] (II) AMD Video driver is signed
[    19.259] (II) fglrx(0): pEnt->device->identifier=0x8f4e4f8
[    19.259] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    19.259] (II) Loading sub module "vgahw"
[    19.259] (II) LoadModule: "vgahw"
[    19.269] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    19.269] (II) Module vgahw: vendor="X.Org Foundation"
[    19.269]     compiled for 1.9.0, module version = 0.1.0
[    19.269]     ABI class: X.Org Video Driver, version 8.0
[    19.269] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    19.269] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    19.269] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    19.269] (==) fglrx(0): Default visual is TrueColor
[    19.269] (==) fglrx(0): RGB weight 888
[    19.269] (II) fglrx(0): Using 8 bits per RGB 
[    19.269] (==) fglrx(0): Buffer Tiling is ON
[    19.269] (II) Loading sub module "fglrxdrm"
[    19.269] (II) LoadModule: "fglrxdrm"
[    19.269] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    19.271] ukiDynamicMajor: found major device number 250
[    19.271] ukiDynamicMajor: found major device number 250
[    19.271] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    19.271] ukiOpenDevice: node name is /dev/ati/card0
[    19.271] ukiOpenDevice: open result is 10, (OK)
[    19.271] ukiOpenByBusid: ukiOpenMinor returns 10
[    19.271] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.271] (==) fglrx(0): NoAccel = NO
[    19.272] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    19.272] (--) fglrx(0): Chipset: "ATI Radeon HD 4550" (Chipset = 0x9540)
[    19.272] (--) fglrx(0): (PciSubVendor = 0x1458, PciSubDevice = 0x21ae)
[    19.272] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    19.272] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    19.272] (--) fglrx(0): MMIO registers at 0xfeae0000
[    19.272] (--) fglrx(0): I/O port at 0x0000d000
[    19.272] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    19.273] (II) fglrx(0): AC Adapter is used
[    19.276] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    19.355] (II) Loading sub module "vbe"
[    19.355] (II) LoadModule: "vbe"
[    19.355] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    19.355] (II) Module vbe: vendor="X.Org Foundation"
[    19.355]     compiled for 1.9.0, module version = 1.1.0
[    19.355]     ABI class: X.Org Video Driver, version 8.0
[    19.355] (II) fglrx(0): VESA BIOS detected
[    19.355] (II) fglrx(0): VESA VBE Version 3.0
[    19.355] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    19.355] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    19.355] (II) fglrx(0): VESA VBE OEM Software Rev: 11.16
[    19.355] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    19.355] (II) fglrx(0): VESA VBE OEM Product: RV710
[    19.355] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    19.378] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    19.378] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
[    19.378] (II) fglrx(0): PCIE card detected
[    19.378] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    19.378] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    19.381] (II) fglrx(0): Using adapter: 1:0.0.
[    19.407] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    19.494] (II) fglrx(0): Interrupt handler installed at IRQ 46.
[    19.494] (II) fglrx(0): RandR 1.2 support is enabled!
[    19.494] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    19.494] (==) fglrx(0): Center Mode is disabled 
[    19.494] (II) Loading sub module "fb"
[    19.494] (II) LoadModule: "fb"
[    19.495] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.495] (II) Module fb: vendor="X.Org Foundation"
[    19.495]     compiled for 1.9.0, module version = 1.0.0
[    19.495]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.495] (==) fglrx(0): Active stereo disabled
[    19.495] (II) Loading sub module "ddc"
[    19.495] (II) LoadModule: "ddc"
[    19.495] (II) Module "ddc" already built-in
[    20.036] (II) fglrx(0): Finished Initialize PPLIB!
[    20.038] (II) fglrx(0): Output DFP1 has no monitor section
[    20.038] (II) fglrx(0): Output DFP2 has no monitor section
[    20.038] (II) fglrx(0): Output CRT1 has no monitor section
[    20.038] (II) fglrx(0): Output CRT2 has no monitor section
[    20.038] (II) Loading sub module "ddc"
[    20.038] (II) LoadModule: "ddc"
[    20.038] (II) Module "ddc" already built-in
[    20.038] (II) fglrx(0): Connected Display0: CRT2
[    20.038] (II) fglrx(0): Display0 EDID data ---------------------------
[    20.038] (II) fglrx(0): Manufacturer: PHL  Model: 862  Serial#: 282971
[    20.038] (II) fglrx(0): Year: 2007  Week: 51
[    20.038] (II) fglrx(0): EDID Version: 1.3
[    20.038] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    20.038] (II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
[    20.038] (II) fglrx(0): Max Image Size [cm]: horiz.: 40  vert.: 25
[    20.038] (II) fglrx(0): Gamma: 2.20
[    20.038] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    20.038] (II) fglrx(0): First detailed timing is preferred mode
[    20.038] (II) fglrx(0): redX: 0.639 redY: 0.342   greenX: 0.297 greenY: 0.614
[    20.038] (II) fglrx(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
[    20.038] (II) fglrx(0): Supported established timings:
[    20.038] (II) fglrx(0): 720x400@70Hz
[    20.038] (II) fglrx(0): 640x480@60Hz
[    20.038] (II) fglrx(0): 640x480@67Hz
[    20.038] (II) fglrx(0): 640x480@72Hz
[    20.038] (II) fglrx(0): 640x480@75Hz
[    20.038] (II) fglrx(0): 800x600@56Hz
[    20.038] (II) fglrx(0): 800x600@60Hz
[    20.038] (II) fglrx(0): 800x600@72Hz
[    20.038] (II) fglrx(0): 800x600@75Hz
[    20.038] (II) fglrx(0): 832x624@75Hz
[    20.038] (II) fglrx(0): 1024x768@60Hz
[    20.038] (II) fglrx(0): 1024x768@70Hz
[    20.038] (II) fglrx(0): 1024x768@75Hz
[    20.038] (II) fglrx(0): 1152x864@75Hz
[    20.038] (II) fglrx(0): Manufacturer's mask: 0
[    20.038] (II) fglrx(0): Supported standard timings:
[    20.038] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    20.038] (II) fglrx(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    20.038] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    20.038] (II) fglrx(0): Supported detailed timing:
[    20.038] (II) fglrx(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
[    20.038] (II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[    20.038] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[    20.038] (II) fglrx(0): Serial No: BZ30751282971
[    20.038] (II) fglrx(0): Monitor name: Philips 190SW
[    20.038] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    20.038] (II) fglrx(0): EDID (in hex):
[    20.038] (II) fglrx(0):     00ffffffffffff00410c62085b510400
[    20.038] (II) fglrx(0):     331101030e2819782aa150a3574c9d25
[    20.038] (II) fglrx(0):     115054bfee80714f9500950f01010101
[    20.038] (II) fglrx(0):     0101010101019a29a0d0518422305098
[    20.038] (II) fglrx(0):     360098ff1000001c000000ff00425a33
[    20.038] (II) fglrx(0):     30373531323832393731000000fc0050
[    20.039] (II) fglrx(0):     68696c697073203139305357000000fd
[    20.039] (II) fglrx(0):     00384c1e530e000a2020202020200072
[    20.039] (II) fglrx(0): End of Display0 EDID data --------------------
[    20.082] (II) fglrx(0): Output DFP1 disconnected
[    20.082] (II) fglrx(0): Output DFP2 disconnected
[    20.082] (II) fglrx(0): Output CRT1 disconnected
[    20.082] (II) fglrx(0): Output CRT2 connected
[    20.082] (II) fglrx(0): Using exact sizes for initial modes
[    20.082] (II) fglrx(0): Output CRT2 using initial mode 1440x900
[    20.082] (II) fglrx(0): DPI set to (96, 96)
[    20.082] (II) fglrx(0): Adapter ATI Radeon HD 4550 has 2 configurable heads and 1 displays connected.
[    20.082] (==) fglrx(0):  PseudoColor visuals disabled
[    20.083] (II) Loading sub module "ramdac"
[    20.083] (II) LoadModule: "ramdac"
[    20.083] (II) Module "ramdac" already built-in
[    20.083] (==) fglrx(0): NoDRI = NO
[    20.083] (==) fglrx(0): Capabilities: 0x00000000
[    20.083] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    20.083] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    20.083] (==) fglrx(0): UseFastTLS=0
[    20.083] (==) fglrx(0): BlockSignalsOnLock=1
[    20.083] (--) Depth 24 pixmap format is 32 bpp
[    20.083] (II) Loading extension ATIFGLRXDRI
[    20.083] (II) fglrx(0): doing swlDriScreenInit
[    20.083] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    20.083] ukiDynamicMajor: found major device number 250
[    20.083] ukiDynamicMajor: found major device number 250
[    20.083] ukiDynamicMajor: found major device number 250
[    20.083] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    20.083] ukiOpenDevice: node name is /dev/ati/card0
[    20.083] ukiOpenDevice: open result is 16, (OK)
[    20.083] ukiOpenByBusid: ukiOpenMinor returns 16
[    20.083] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    20.083] (II) fglrx(0): [uki] DRM interface version 1.0
[    20.083] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    20.083] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    20.083] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb77a7000
[    20.083] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    20.083] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    20.083] (II) fglrx(0): swlDriScreenInit done
[    20.083] (II) fglrx(0): Kernel Module Version Information:
[    20.083] (II) fglrx(0):     Name: fglrx
[    20.083] (II) fglrx(0):     Version: 8.78.30
[    20.083] (II) fglrx(0):     Date: Sep 20 2010
[    20.083] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    20.083] (II) fglrx(0): Kernel Module version matches driver.
[    20.083] (II) fglrx(0): Kernel Module Build Time Information:
[    20.083] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.35-25-generic
[    20.084] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    20.084] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    20.084] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    20.084] (II) fglrx(0): [uki] register handle = 0x00004000
[    20.096] (II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
[    20.096] (II) fglrx(0): DRI initialization successfull
[    20.096] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010a8000
[    20.096] (II) fglrx(0): FBMM initialized for area (0,0)-(1664,2624)
[    20.096] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1664,1664) (front color buffer - assumption)
[    20.096] (II) fglrx(0): Largest offscreen area available: 1664 x 960
[    20.097] (==) fglrx(0): Backing store disabled
[    20.097] (II) Loading extension FGLRXEXTENSION
[    20.097] (==) fglrx(0): DPMS enabled
[    20.097] (II) fglrx(0): Initialized in-driver Xinerama extension
[    20.097] (**) fglrx(0): Textured Video is enabled.
[    20.097] (II) LoadModule: "glesx"
[    20.097] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    20.098] (II) Module glesx: vendor="X.Org Foundation"
[    20.098]     compiled for 1.8.99.905, module version = 1.0.0
[    20.098] (II) Loading extension GLESX
[    20.098] (II) fglrx(0): GLESX enableFlags = 528
[    20.098] (II) fglrx(0): GLESX is enabled
[    20.098] (II) fglrx(0): Acceleration enabled
[    20.099] (II) LoadModule: "amdxmm"
[    20.099] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    20.099] (II) Module amdxmm: vendor="X.Org Foundation"
[    20.099]     compiled for 1.8.99.905, module version = 1.0.0
[    20.099] (II) Loading extension AMDXVOPL
[    20.100] (II) fglrx(0): UVD2 feature is available
[    20.101] (II) fglrx(0): Enable composite support successfully
[    20.101] (II) fglrx(0): X context handle = 0x1
[    20.101] (II) fglrx(0): [DRI] installation complete
[    20.101] (==) fglrx(0): Silken mouse enabled
[    20.102] (==) fglrx(0): Using HW cursor of display infrastructure!
[    20.102] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    20.205] (--) RandR disabled
[    20.205] (II) Initializing built-in extension Generic Event Extension
[    20.205] (II) Initializing built-in extension SHAPE
[    20.205] (II) Initializing built-in extension MIT-SHM
[    20.205] (II) Initializing built-in extension XInputExtension
[    20.205] (II) Initializing built-in extension XTEST
[    20.205] (II) Initializing built-in extension BIG-REQUESTS
[    20.205] (II) Initializing built-in extension SYNC
[    20.205] (II) Initializing built-in extension XKEYBOARD
[    20.205] (II) Initializing built-in extension XC-MISC
[    20.205] (II) Initializing built-in extension SECURITY
[    20.205] (II) Initializing built-in extension XINERAMA
[    20.205] (II) Initializing built-in extension XFIXES
[    20.205] (II) Initializing built-in extension RENDER
[    20.205] (II) Initializing built-in extension RANDR
[    20.205] (II) Initializing built-in extension COMPOSITE
[    20.205] (II) Initializing built-in extension DAMAGE
[    20.205] (II) Initializing built-in extension GESTURE
[    20.225] ukiDynamicMajor: found major device number 250
[    20.225] ukiDynamicMajor: found major device number 250
[    20.225] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    20.225] ukiOpenDevice: node name is /dev/ati/card0
[    20.225] ukiOpenDevice: open result is 17, (OK)
[    20.225] ukiOpenByBusid: ukiOpenMinor returns 17
[    20.225] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    20.299] (II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
[    20.299] (II) GLX: Initialized DRI GL provider for screen 0
[    20.299] (II) fglrx(0): Enable the clock gating!
[    20.299] (II) fglrx(0): Setting screen physical size to 380 x 238
[    20.315] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.324] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.324] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.324] (II) LoadModule: "evdev"
[    20.324] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.325] (II) Module evdev: vendor="X.Org Foundation"
[    20.325]     compiled for 1.9.0, module version = 2.3.2
[    20.325]     Module class: X.Org XInput Driver
[    20.325]     ABI class: X.Org XInput driver, version 11.0
[    20.325] (**) Power Button: always reports core events
[    20.325] (**) Power Button: Device: "/dev/input/event1"
[    20.336] (II) Power Button: Found keys
[    20.336] (II) Power Button: Configuring as keyboard
[    20.336] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.336] (**) Option "xkb_rules" "evdev"
[    20.336] (**) Option "xkb_model" "evdev"
[    20.336] (**) Option "xkb_layout" "it"
[    20.338] (II) XKB: reuse xkmfile /var/lib/xkb/server-35DF0DEC488035CD7337E5EF69F018BFAFADCAC5.xkm
[    20.340] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.340] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.340] (**) Power Button: always reports core events
[    20.340] (**) Power Button: Device: "/dev/input/event0"
[    20.352] (II) Power Button: Found keys
[    20.352] (II) Power Button: Configuring as keyboard
[    20.352] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.352] (**) Option "xkb_rules" "evdev"
[    20.352] (**) Option "xkb_model" "evdev"
[    20.352] (**) Option "xkb_layout" "it"
[    20.355] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event2)
[    20.355] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    20.355] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    20.355] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event2"
[    20.368] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    20.368] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    20.368] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    20.368] (**) Option "xkb_rules" "evdev"
[    20.368] (**) Option "xkb_model" "evdev"
[    20.368] (**) Option "xkb_layout" "it"
[    20.369] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event3)
[    20.369] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev pointer catchall"
[    20.369] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    20.369] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    20.369] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event3"
[    20.384] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 9 mouse buttons
[    20.384] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[    20.384] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[    20.384] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y relative axes
[    20.384] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[    20.384] (II) evdev-grail: failed to open grail, no gesture support
[    20.384] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    20.384] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[    20.384] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    20.384] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[    20.384] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.384] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    20.384] (**) Option "xkb_rules" "evdev"
[    20.384] (**) Option "xkb_model" "evdev"
[    20.384] (**) Option "xkb_layout" "it"
[    20.385] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for relative axes.
[    20.385] (WW) Microsoft Microsoft® 2.4GHz Transceiver v6.0: ignoring absolute axes.
[    20.385] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/mouse0)
[    20.385] (II) No input driver/identifier specified (ignoring)
[    20.385] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event4)
[    20.386] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    20.386] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    20.386] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event4"
[    20.400] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 1 mouse buttons
[    20.400] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[    20.400] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[    20.400] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[    20.400] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y absolute axes
[    20.400] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    20.400] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[    20.400] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    20.400] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[    20.400] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.400] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    20.400] (**) Option "xkb_rules" "evdev"
[    20.400] (**) Option "xkb_model" "evdev"
[    20.400] (**) Option "xkb_layout" "it"
[    20.401] (EE) Microsoft Microsoft® 2.4GHz Transceiver v6.0: failed to initialize for relative axes.
[    20.401] (WW) Device 'Microsoft Microsoft® 2.4GHz Transceiver v6.0' has 37 axes, only using first 36.
[    20.401] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for absolute axes.
[    20.401] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/js0)
[    20.401] (II) No input driver/identifier specified (ignoring)
[    20.402] (II) config/udev: Adding input device Microsoft® LifeCam VX-2000 (/dev/input/event5)
[    20.402] (**) Microsoft® LifeCam VX-2000: Applying InputClass "evdev keyboard catchall"
[    20.402] (**) Microsoft® LifeCam VX-2000: always reports core events
[    20.402] (**) Microsoft® LifeCam VX-2000: Device: "/dev/input/event5"
[    20.416] (II) Microsoft® LifeCam VX-2000: Found keys
[    20.416] (II) Microsoft® LifeCam VX-2000: Configuring as keyboard
[    20.416] (II) XINPUT: Adding extended input device "Microsoft® LifeCam VX-2000" (type: KEYBOARD)
[    20.416] (**) Option "xkb_rules" "evdev"
[    20.416] (**) Option "xkb_model" "evdev"
[    20.416] (**) Option "xkb_layout" "it"
[    20.452] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    21.493] (II) fglrx(0): EDID vendor "PHL", prod id 2146
[    21.493] (II) fglrx(0): Using EDID range info for horizontal sync
[    21.493] (II) fglrx(0): Using EDID range info for vertical refresh
[    21.493] (II) fglrx(0): Printing DDC gathered Modelines:
[    21.493] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    21.493] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.493] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.493] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.493] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    21.493] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    21.493] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.493] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    21.493] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.493] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    21.493] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.493] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    21.493] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.493] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    21.493] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    21.493] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    21.840] (II) fglrx(0): EDID vendor "PHL", prod id 2146
[    21.840] (II) fglrx(0): Using hsync ranges from config file
[    21.840] (II) fglrx(0): Using vrefresh ranges from config file
[    21.840] (II) fglrx(0): Printing DDC gathered Modelines:
[    21.840] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    21.840] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.840] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.840] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.840] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    21.840] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    21.840] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.840] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    21.840] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.841] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    21.841] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.841] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    21.841] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.841] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    21.841] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    21.841] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    22.191] (II) fglrx(0): EDID vendor "PHL", prod id 2146
[    22.191] (II) fglrx(0): Using hsync ranges from config file
[    22.191] (II) fglrx(0): Using vrefresh ranges from config file
[    22.191] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.191] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    22.191] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.191] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    22.192] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    22.192] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    22.192] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    22.192] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.192] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.192] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    22.192] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    22.192] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.192] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.192] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.192] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    22.192] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    22.192] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    22.551] (II) fglrx(0): EDID vendor "PHL", prod id 2146
[    22.551] (II) fglrx(0): Using hsync ranges from config file
[    22.551] (II) fglrx(0): Using vrefresh ranges from config file
[    22.551] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.551] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    22.551] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.551] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    22.551] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    22.551] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    22.551] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    22.551] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.551] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.552] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    22.552] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    22.552] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.552] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.552] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.552] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    22.552] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    22.552] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    28.596] (II) fglrx(0): EDID vendor "PHL", prod id 2146
[    28.596] (II) fglrx(0): Using hsync ranges from config file
[    28.596] (II) fglrx(0): Using vrefresh ranges from config file
[    28.596] (II) fglrx(0): Printing DDC gathered Modelines:
[    28.596] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    28.596] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.596] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.596] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.596] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    28.596] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    28.596] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.596] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    28.596] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.596] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    28.596] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.596] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    28.596] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.596] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    28.596] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.596] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)

```

Hope this can help.

Bye

---

### Post by robsoles on 2011-02-16
It occurs to me that a squiz at your /etc/X11/xorg.conf files might be horribly handy too:```
cat /etc/X11/xorg.conf
```

---

### Post by charlie_b on 2011-02-16
I have had this problem too, not very often but it happens. When it does I just switch to another workspace (bottom right hand of screen) then switch back to Desk 1. This fixes the problem for me.

---

### Post by Nico34 on 2011-02-16
> **charlie_b said:**
> I have had this problem too, not very often  but it happens. When it does I just switch to another workspace (bottom  right hand of screen) then switch back to Desk 1. This fixes the problem  for me.
Tried that but it doesn't work; the "anomaly" just seems to be on a upper layer than the normal screen; weird...


> **robsoles said:**
> It occurs to me that a squiz at your /etc/X11/xorg.conf files might be horribly handy too:```
cat /etc/X11/xorg.conf
```
Thanks robsoles,

here is what I get:

```
nico@ubuntu:~$ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

```

---

### Post by robsoles on 2011-02-16
Certainly nothing too complicated or outrageous in your xorg.conf file, I think your guess re. compositing is the best guess so far...

---

### Post by Nico34 on 2011-02-16
> **robsoles said:**
> Certainly nothing too complicated or outrageous in your xorg.conf file, I think your guess re. compositing is the best guess so far...
Or maybe could it be a hardware-related issue that influences Compositing?

I'm actually having another "view" problem.
At boot I don't get the regular Ubuntu splash screen, but a black screen with ```
[17.XXXXX] cannot find UAC_HEADER
``` written on top and then a low-resolution splash without the logo.

I have always had the same issue in all my Ubuntu installations and even with Kubuntu and Xubuntu.
When I turn off the computer I got the low-reso screen again with messages below (didn't manage to make a picture).

Could it all be caused by my video card Radeon HD4550? (but I had no issues in Windows XP)

---

### Post by robsoles on 2011-02-16
> **Nico34 said:**
> ...

Could it all be caused by my video card Radeon HD4550? (but I had no issues in Windows XP)

Very likely. (A manufacturer releasing a driver dependent product without ***working*** drivers for Windows remains a lot less likely than a manufacturer releasing said product without decent Linux support - this will turn in time but when is difficult to calculate...)

---

### Post by Nico34 on 2011-02-16
> **robsoles said:**
> Very likely. (A manufacturer releasing a driver dependent product without ***working*** drivers for Windows remains a lot less likely than a manufacturer releasing said product without decent Linux support - this will turn in time but when is difficult to calculate...)
I hope it's not too early to say so, but you are probably right about the issue being caused by the proprietary drivers (I should have followed matt_symes advice...).

I'm currently re-installing Ubuntu after I totally messed up my previous system: after trying different combinations/options with the window/compositing managers, I had the crazy idea to update the ATI drivers without uninstalling the current ones; I finally arrived to a situation where on every reboot nautilus opened an infinite number of instances; I surrendered after I uninstalled it  and lost access to the desktop :D

I guess in the future I will have to be a little wiser and avoid installing things I'm not able to control :mrgreen:

Anyway, with the open drivers I have now the regular Ubuntu splash screen back and the command lines have disappeared.

---

### Post by alphacrucis2 on 2011-02-16
> **Nico34 said:**
> I hope it's not too early to say so, but you are probably right about the issue being caused by the proprietary drivers (I should have followed matt_symes advice...).

I'm currently re-installing Ubuntu after I totally messed up my previous system: after trying different combinations/options with the window/compositing managers, I had the crazy idea to update the ATI drivers without uninstalling the current ones; I finally arrived to a situation where on every reboot nautilus opened an infinite number of instances; I surrendered after I uninstalled it  and lost access to the desktop :D

I guess in the future I will have to be a little wiser and avoid installing things I'm not able to control :mrgreen:

Anyway, with the open drivers I have now the regular Ubuntu splash screen back and the command lines have disappeared.

It isn't too hard to install the latest version of fglrx from the AMD website but you do need to purge the old version first. You should install the new one using the buildpkg method as documented in the binary driver howto. That means that the package manager will know which version of fglrx you have installed. The version in the repos is from last September but AMD release a new Catalyst/fglrx every month and many bugs get fixed. The current one is for January but the February one will be out soon and worth a try. (Actually I see AMD have already released the February Catalyst update. Must try it out myself.

---

### Post by migs73 on 2011-02-17
My X11 file is quite different, but I don't have any proprietry drivers fro my graphics

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri2"
	Load  "record"
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  330   210	# mm
	Identifier   "Monitor0"
	VendorName   "LPL"
	ModelName    "a900"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "CustomEDID"         	# [<str>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ClockGating"        	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "ATOMTVOut"          	# [<bool>]
        #Option     "R4xxATOM"           	# [<bool>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "DynamicPM"          	# [<bool>]
        #Option     "NewPLL"             	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

and for the sake of completeness, this is my graphics card;

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

```

---

### Post by robsoles on 2011-02-17
I should probably admit that for all the brilliant ride my system gives me it has those console messages over the shutdown screen and looks positively ugly whilst shutting down but I halfway expect that sort of thing and I definitely don't care - I should probably post my xorg.conf file too though:```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer X243H"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG W2053"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by hansolo4949 on 2011-02-17
Perhaps your graphics driver/card is the issue? Maybe when things get bogged down that happens....does it stay that way, or goi away after a few seconds?

---

### Post by Nico34 on 2011-02-17
Back :D

I can definitely say that the proprietary drivers are not the issue (though by not installing them and keeping the open ones I solved my splash screen problem :)).

I'm now pretty sure it's something that is directly related to Compositing and/or with Compiz or Metacity; I cannot install any dock on my desktop (tried AWN and Docky).

In a few words, rolled back to where I started from: in need for help...

I haven't tried to set Compiz as default window manager, mostly because I don't know how to do it :rolleyes:

---

### Post by robsoles on 2011-02-17
> **Nico34 said:**
> ...

I'm now pretty sure it's something that is directly related to Compositing and/or with Compiz or Metacity; I cannot install any dock on my desktop (tried AWN and Docky).

...

**What if it's AWN or Docky themselves entirely?** (or perhaps a dependency they specifically share that isn't installed/loaded just by gnome+metacity+compiz)

I run neither of those, have compiz settings enabled to a fair degree and pretty sure metacity is my window dresser on the desktop PC I use at home.

As I posted before: It's video performance 'in session' doesn't artifact or anything else to complain about, seems like a 'feature' of the proprietary drivers that it turns uglyish while shutting down but the startup splash (vanilla) is pretty enough.


Sorry, I hate Docky style apps and won't even temporarily install one to check if it starts a visual (or other) problem on my setup.

---

