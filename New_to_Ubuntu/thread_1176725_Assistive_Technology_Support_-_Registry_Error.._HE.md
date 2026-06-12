---
title: "Assistive Technology Support - Registry Error.. HELP!"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by crjackson on 2009-06-02
Today I booted my Hardy 8.04.2 32-bit laptop system and was greeted with the following error.

> Assistive Technology Support has be requested for this session, but no Assistive Technology Registry has been found. Please insure AT-SPI is installed.

I rebooted several times and reinstalled the AT-SPI support but I still get the error.

Can someone help me make this go away.

Here is the actual error:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(seahorse-agent:5894): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(seahorse-agent:5894): atk-bridge-WARNING **: IOR not set.

(seahorse-agent:5894): atk-bridge-WARNING **: Could not locate registry
Xlib:  extension "XEVIE" missing on display ":0.0".
SESSION_MANAGER=local/charles-laptop:/tmp/.ICE-unix/5894
** Message: another SSH agent is running at: /tmp/ssh-Idkdsq5894/agent.5894
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Initializing nautilus-share extension
seahorse nautilus module initialized
Window manager warning: Failed to read saved session file /home/charles/.metacity/sessions/default0.ms: Failed to open file '/home/charles/.metacity/sessions/default0.ms': No such file or directory

** (gsynaptics-init:6101): WARNING **: Using synclient

** (<unknown>:5991): WARNING **: Failed to send buffer

** (<unknown>:5991): WARNING **: Failed to send buffer


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Unknown parameter CoastingSpeedThreashold
11
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_ACAD

(nautilus:6070): GLib-GObject-WARNING **: Two different plugins tried to register 'NautilusBurn'.

(nautilus:6070): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(nautilus:6070): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed
Throttle level is 5

** (nautilus:6070): WARNING **: Unable to add monitor: Not supported
evolution-alarm-notify-Message: Setting timeout for 29753 1244001600 1243971847
evolution-alarm-notify-Message:  Wed Jun  3 00:00:00 2009

evolution-alarm-notify-Message:  Tue Jun  2 15:44:07 2009


(gnome-panel:6068): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/charles/.recently-used.xbel', but the parser failed: Error reading file '/home/charles/.recently-used.xbel': Is a directory.

(gnome-panel:6068): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(soffice:6331): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gsignal.c:1669: signal `monitors-changed' is invalid for instance `0x807d120'
** Message: <info>  Forcing device '/org/freedesktop/NetworkManager/Devices/wlan0'


** (nm-applet:6117): CRITICAL **: nm_gconf_wso_set_key: assertion `key != NULL' failed

** (nm-applet:6117): WARNING **: <WARN>  real_write_secrets_cb(): Error saving secret for wireless network 'Buffalo' in keyring: 5


** (nm-applet:6117): CRITICAL **: nm_gconf_wso_set_key: assertion `key != NULL' failed

** (nm-applet:6117): WARNING **: <WARN>  real_write_secrets_cb(): Error saving secret for wireless network 'Buffalo' in keyring: 5

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
  PID TTY          TIME CMD
 6050 ?        00:00:00 pulseaudio

** (<unknown>:5991): WARNING **: Failed to send buffer
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:6070): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/charles/.recently-used.xbel', but the parser failed: Error reading file '/home/charles/.recently-used.xbel': Is a directory.

(nautilus:6070): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

(nautilus:6070): Gtk-WARNING **: Attempting to store changes into `/home/charles/.recently-used.xbel', but failed: Failed to rename file '/home/charles/.recently-used.xbel.OEYRUU' to '/home/charles/.recently-used.xbel': g_rename() failed: Is a directory

(gedit:8034): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/charles/.recently-used.xbel', but the parser failed: Error reading file '/home/charles/.recently-used.xbel': Is a directory.

(gedit:8034): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

[B][SIZE="4"]UPDATE:

Okay, so I went to the System>Preferences>Assistive Technologies applet and disabled it for now. The error seems to have disappeared for the time being, but what is the permanent fix for this?

I've searched the forums, I've googled the issue too. I found a few others who were having the problem in past versions, but no solutions.

I'm standing-by for someone to jump in with some information here.[/SIZE][/B]

---

### Post by crjackson on 2009-06-02
Not even a bite yet?

---

### Post by crjackson on 2009-06-05
bump

---

### Post by crjackson on 2009-06-07
bump

---

### Post by crjackson on 2009-06-09
bump

---

### Post by crjackson on 2009-06-10
bump

---

### Post by crjackson on 2009-06-11
bump

---

### Post by crjackson on 2009-06-14
bump

---

### Post by crjackson on 2009-06-18
bump

---

### Post by crjackson on 2009-06-20
bump

---

### Post by crjackson on 2009-06-26
bump

---

### Post by crjackson on 2009-06-28
bump

---

### Post by Sef on 2009-06-29
Did you turn on any assistive technology?

---

### Post by crjackson on 2009-07-05
> **Sef said:**
> Did you turn on any assistive technology?

I originally turned on reduced resources and killed animations because my video card is poorly supported in 9.04.

Then I found that with this setting, dragging any window will stall video and sound playback.

So I turned on the interface accessibility option which fixes that.  All is well until a reboot, then I get errors and find that interface accessibility is disabled once again.

---

### Post by nema.arpit on 2009-10-16
Bump
looking for a solution
I need to enable "Simulated Secondary Click"

---

### Post by falconindy on 2009-10-16
Unrelated topic is completely unrelated. What you seek is under System -> Preference -> Mouse -> Accessibility tab.

---

### Post by nema.arpit on 2009-10-17
I am sorry I didn't explain myself fully.
Whenever I enable it (I already knew where the option is),it tells me to logout to apply,thats fine and all.It turns on fine after a re-login.[COLOR=Red]The trouble starts at reboot[/COLOR], at every reboot I get the same error as the OP and further more the SS click becomes disabled again.So my problem is quite similar to the OP atleast.

---

### Post by crjackson on 2009-10-17
open up a terminal and enter:
```
gconf-editor
```

go to

/desktop/gnome/interface/accessibility

look at the viewing pane on the right and put a check mark in the accessibility box.

then go to the file context menu and select quit.  Log off and back on again and see if this helps.

I was playing around on mine and that combined with some updates or other tinkering fixed it.  Sorry I can't be more specific, but I was surprised with it started working correctly. I think that's what did it but I'm not 100% sure.

---

