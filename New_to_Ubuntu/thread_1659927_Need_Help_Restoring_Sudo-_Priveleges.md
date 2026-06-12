---
title: "Need Help Restoring Sudo- Priveleges"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by kOjO619 on 2011-01-04
Hi all -

Last year, I installed Ubuntu 10.04 on my z61t Thinkpad & have been having a lot of fun with the O/S & learning new things about computers, how Windoze sucks, etc. However, recently I transgressed & while having a flash of brilliance, removed myself from the admin group. And yes, was the last user. Having scoured the countless blogs, tutorials, & tried a few, to no avail. Tha latest was my booting thru recovery at the root shell level to edit the sudoers file - failed. Then tried to just add my name (adduser) only to be told my name didn't exist. You more seasoned users know better than I how perilous life can be with no (sudo). In a word....help !!

Any sure fire ways to get my (sudo) restored would be greatly appreciated - thx.

---

### Post by Hippytaff on 2011-01-04
hi and welcome

have you tried login in with the username root? boot and select recovery mode (or is it rescue mode :? ) from the menu. choose terminal with networking and try username root, and your original password, then add yourself to the admin group or the sudoers file.

---

### Post by kOjO619 on 2011-01-04
Hi & thanks H/T -

No, I wasn't even aware of username root. Sorta thought root was just root...  :) But I will try it & report back what happens... Sorta makes me regret not personally installing 10.04 & XPpro, as I undoubtedly missed on some things. Will go try this & chime in shortly - thanks

---

### Post by kOjO619 on 2011-01-06
Hi -I'm back & sorry for lag in response time, as now I am stressing.
Having booted into recovery mode at root level w/networking - that did not work either.
Initially the computer started to try & communicate to the Internet Sys Corp (???) via a modem
that i dont think i authorized, thru Ebox, then eth0, wlan0, various port sequentially & failed. I tried to add my user name only to be told again - my name didn't exist. I tried to list admin, usr, users, & was told the files didn't exist. I then just put in 'root,' & was told that the program was not installed...... I don't want to have to reinstall just yet...Any other tips out there ??  -sigh-:confused:

---

### Post by wojox on 2011-01-06
Try this [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by kOjO619 on 2011-01-06
I'm back -

Tried your suggestion...Booted down to root shell then listed users only to find one
entry - a backup user name I had created. But of course, it garnered the same reply
that adding my user name received - 'sorry the underlying mechanism (sudo) doesn't
authorize this action..... This whole situation is looking real bleak. I dunno if this is relevant,
but I know that damn EBox has assigned some file as root; some .tmp file. How is that possible ???:confused:

---

### Post by wojox on 2011-01-06
Really. If your in a root shell you wouldn't need sudo.

---

### Post by kOjO619 on 2011-01-06
Hi -

My thoughts exactly.... However I have seen in a few tutorials that when booting into that root shell
(via recovery mode) to use syntax like sudo visudo before you edit a sudoers file, or even add a user.
Nevertheless, it's not granting my sudo-status even after i successfully added my name as admin in the current Sudoer's file. How can it not grant me the status ?? Doesn't make since to me. As an aside, the
backup user name I made for an emergency situation is not receiving (sudo) priveleges either.

---

### Post by kOjO619 on 2011-01-06
Hi all -

Still confused as to why the suggestions offered thus far haven't worked out
favorably...Did some looking around in my files & came across one called (Xsession
Errors). Inside was, as it said, a bunch of errors that have gone wrong - daily, I guess ??

At any rate, given all tha 'Warnings' & Criticals,' could this shed some light on why or where
my sudo rights have gone... ?? What follows is a screen print of the file....Any wisdom lent is of course appreciated.  Thx.....


/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-of19eU
GNOME_KEYRING_CONTROL=/tmp/keyring-of19eU
SSH_AUTH_SOCK=/tmp/keyring-of19eU/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-of19eU
SSH_AUTH_SOCK=/tmp/keyring-of19eU/ssh

(gnome-settings-daemon:4051): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
gnome-session[4003]: WARNING: Could not launch application '106b07a17324b1ea17129436041340454700000014110034.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)

(polkit-gnome-authentication-agent-1:4076): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:4076): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:4074): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x22dfb20'

(gnome-settings-daemon:4051): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(gnome-settings-daemon:4051): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(gnome-settings-daemon:4051): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(gnome-settings-daemon:4051): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(gnome-settings-daemon:4051): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

** (nm-applet:4083): WARNING **: Invalid connection /system/networking/connections/6: 'NMSettingCdma' / 'number' invalid: 1
** (nm-applet:4083): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4083): DEBUG: old state indicates that this was not a disconnect 0

** (gnome-screensaver:4110): WARNING **: screensaver already running in this session
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
Unable to open desktop file /home/user/bluetooth-properties.desktop for panel launcher: No such file or directory

** (gnome-settings-daemon:4051): CRITICAL **: setup_bg: assertion `manager->priv->bg == NULL' failed

(gnome-settings-daemon:4051): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/AppletPlugin.py", line 105, in _load
    self.on_load(applet)
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/PulseAudio.py", line 115, in on_load
    if int(version.split(".")[2]) < 15:
ValueError: invalid literal for int() with base 10: '21-63-gd3efa-dirty'
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

(nm-applet:4083): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
Initializing nautilus-gdu extension

(nautilus:4079): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
evolution-alarm-notify-Message: Setting timeout for 81308 1294444800 1294363492
evolution-alarm-notify-Message: Setting timeout for 81308 1294444800 1294363492
evolution-alarm-notify-Message:  Fri Jan  7 16:00:00 2011

evolution-alarm-notify-Message:  Thu Jan  6 17:24:52 2011

evolution-alarm-notify-Message:  Fri Jan  7 16:00:00 2011

evolution-alarm-notify-Message:  Thu Jan  6 17:24:52 2011


(evolution-alarm-notify:4179): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so [/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-mully-plugin.so [/usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so [/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
!!! Error reading feed
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so [/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-mully-plugin.so [/usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so [/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]

** (update-notifier:4326): WARNING **: log file empty (logrotate?) /var/log/dpkg.log


** (update-notifier:4326): WARNING **: log file empty (logrotate?) /var/log/apt/term.log

** (update-notifier:4326): DEBUG: Skipping reboot required
** (nm-applet:4083): DEBUG: going for offline with icon: notification-network-disconnected
ERROR:dbus.proxies:Introspect error on :1.38:/org/freedesktop/Hal/devices/usb_device_106c_3b06_000000000002_if0_scsi_host: dbus.exceptions.DBusException: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_106c_3b06_000000000002_if0_scsi_host
** (nm-applet:4083): DEBUG: foo_client_state_changed_cb
** (nm-applet:4083): DEBUG: foo_client_state_changed_cb
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Help !!

---

### Post by wojox on 2011-01-06
Did you try that other link [Troubleshooting Sudo]("http://www.psychocats.net/ubuntu/sudo")

---

### Post by kOjO619 on 2011-01-07
[B]Hi Wojox -

Thank you for your patience in working with me !!!

Successfully edited the 'sudoers & group' files at the root shell prompt in Recovery Mode.
I learned some things - type commands exactly as I see them (incl. spacing), The name
(user) might be the name assigned to me as I did not perform the 10.04 installation, & I
removed (eBox) from the _adm_ line as I saw no reason for it to be there. Incidentally, I reviewed the group lists several times & did not see an (admin) line, jus (adm). Trust that
is nothing to be alarmed about. Yet, STILL upon running my Synaptic, do I receive the:

Failed to run /usr/sbin/synaptic as user root. Not authorized by (sudo) to run this, blah..blah.

But I know we're close on account of my laptop acting & behaving more close to normal than it has been...... So what is failing to run this particular file ???
[/B]

---

