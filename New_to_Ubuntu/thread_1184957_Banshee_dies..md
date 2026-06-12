---
title: "Banshee dies."
date: 2009-06-11
forum: New to Ubuntu
---

### Post by insub2 on 2009-06-11
Banshee Keeps crashing on me :(

Here is the output, any ideas?

```
An unhandled exception was thrown: Array index is out of range.

at NDesk.DBus.MessageReader.MarshalUInt (byte*) <0x0002d>
at NDesk.DBus.MessageReader.ReadUInt32 () <0x00018>
at NDesk.DBus.MessageReader.ReadValue (NDesk.DBus.DType) <0x00113>
at NDesk.DBus.MessageReader.ReadValue (System.Type) <0x00235>
at NDesk.DBus.MessageHelper.GetDynamicValues (NDesk.DBus.Message,System.Reflection.ParameterInfo[]) <0x000d5>
at NDesk.DBus.Connection.HandleSignal (NDesk.DBus.Message) <0x000f4>
at NDesk.DBus.Connection.DispatchSignals () <0x0003c>
at NDesk.DBus.Connection.Iterate () <0x0002c>
at <Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x0002a>
at (wrapper native-to-managed) <Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x00049>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.Gui.GtkBaseClient.Run () <0x00035>
at Banshee.Gui.GtkBaseClient.Startup () <0x00031>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x000a2>


.NET Version: 2.0.50727.42
OS Version: Unix 2.6.28.11

Assembly Version Information:

System.Web (2.0.0.0)
avahi-sharp (1.0.0.0)
Mono.Zeroconf.Providers.Avahi (2.0.0.76)
Mono.Zeroconf (2.0.0.76)
Mtp (1.4.0.0)
ipod-sharp (0.0.1.0)
Banshee.Dap.Mtp (1.4.0.0)
Banshee.Dap.MassStorage (1.4.0.0)
taglib-sharp (2.0.3.2)
Mono.Media (1.4.0.0)
Banshee.InternetRadio (1.4.0.0)
Banshee.PlayQueue (1.4.0.0)
Banshee.FileSystemQueue (1.4.0.0)
Banshee.CoverArt (1.4.0.0)
Migo (1.4.0.0)
Banshee.Podcasting (1.4.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.4.0.0)
System.Configuration (2.0.0.0)
MusicBrainz (1.4.0.0)
Banshee.AudioCd (1.4.0.0)
Lastfm (1.4.0.0)
Banshee.Lastfm (1.4.0.0)
Banshee.Bookmarks (1.4.0.0)
Banshee.Daap (1.4.0.0)
Banshee.MultimediaKeys (1.4.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.4.0.0)
Banshee.Dap.Ipod (1.4.0.0)
Banshee.Dap (1.4.0.0)
Banshee.Hal (1.4.0.0)
Banshee.Unix (1.4.0.0)
Banshee.GStreamer (1.4.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.4.0.0)
Banshee.NowPlaying (1.4.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
System.Xml (2.0.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.4.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (1.4.0.0)
Nereid (1.4.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Banshee.Core (1.4.0.0)
System (2.0.0.0)
Hyena (1.4.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.4.0.0)
Banshee (1.4.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.28-11-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

[/etc/debian_version]
5.0


```

---

### Post by directhex on 2009-06-11
> **insub2 said:**
> Banshee Keeps crashing on me :(

Here is the output, any ideas?

```
An unhandled exception was thrown: Array index is out of range.

at NDesk.DBus.MessageReader.MarshalUInt (byte*) <0x0002d>
at NDesk.DBus.MessageReader.ReadUInt32 () <0x00018>
at NDesk.DBus.MessageReader.ReadValue (NDesk.DBus.DType) <0x00113>
at NDesk.DBus.MessageReader.ReadValue (System.Type) <0x00235>
at NDesk.DBus.MessageHelper.GetDynamicValues (NDesk.DBus.Message,System.Reflection.ParameterInfo[]) <0x000d5>
at NDesk.DBus.Connection.HandleSignal (NDesk.DBus.Message) <0x000f4>
at NDesk.DBus.Connection.DispatchSignals () <0x0003c>
at NDesk.DBus.Connection.Iterate () <0x0002c>
at <Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x0002a>
at (wrapper native-to-managed) <Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x00049>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.Gui.GtkBaseClient.Run () <0x00035>
at Banshee.Gui.GtkBaseClient.Startup () <0x00031>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x000a2>


.NET Version: 2.0.50727.42
OS Version: Unix 2.6.28.11

Assembly Version Information:

System.Web (2.0.0.0)
avahi-sharp (1.0.0.0)
Mono.Zeroconf.Providers.Avahi (2.0.0.76)
Mono.Zeroconf (2.0.0.76)
Mtp (1.4.0.0)
ipod-sharp (0.0.1.0)
Banshee.Dap.Mtp (1.4.0.0)
Banshee.Dap.MassStorage (1.4.0.0)
taglib-sharp (2.0.3.2)
Mono.Media (1.4.0.0)
Banshee.InternetRadio (1.4.0.0)
Banshee.PlayQueue (1.4.0.0)
Banshee.FileSystemQueue (1.4.0.0)
Banshee.CoverArt (1.4.0.0)
Migo (1.4.0.0)
Banshee.Podcasting (1.4.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.4.0.0)
System.Configuration (2.0.0.0)
MusicBrainz (1.4.0.0)
Banshee.AudioCd (1.4.0.0)
Lastfm (1.4.0.0)
Banshee.Lastfm (1.4.0.0)
Banshee.Bookmarks (1.4.0.0)
Banshee.Daap (1.4.0.0)
Banshee.MultimediaKeys (1.4.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.4.0.0)
Banshee.Dap.Ipod (1.4.0.0)
Banshee.Dap (1.4.0.0)
Banshee.Hal (1.4.0.0)
Banshee.Unix (1.4.0.0)
Banshee.GStreamer (1.4.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.4.0.0)
Banshee.NowPlaying (1.4.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
System.Xml (2.0.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.4.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (1.4.0.0)
Nereid (1.4.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Banshee.Core (1.4.0.0)
System (2.0.0.0)
Hyena (1.4.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.4.0.0)
Banshee (1.4.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.28-11-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

[/etc/debian_version]
5.0


```

Please open a bug on the upstream bug tracker, they'll be able to help

That said, have you tried installing 1.5.0 from the banshee-unstable-team PPA?

---

### Post by insub2 on 2009-06-24
Did the whole upgrade to 1.5 and it still crashes. :(:(:(

---

### Post by directhex on 2009-06-24
> **insub2 said:**
> Did the whole upgrade to 1.5 and it still crashes. :(:(:(

Okay, sounds weird. Try running "banshee --debug" and pasting everything into a new bug on bugzilla.gnome.org

---

