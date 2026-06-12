---
title: "Major problem, Fatal Error on F-Spot"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-09-03
These are the error details

An unhandled exception was thrown: Object reference not set to an instance of an object

  at FileImportBackend.Prepare () [0x00000] 
  at ImportCommand.DoImport (.ImportBackend imp) [0x00000] 
  at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags, Boolean copy) [0x00000] 
  at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags) [0x00000] 
  at FSpot.CameraFileSelectionDialog.ImportFiles () [0x00000] 
  at FSpot.CameraFileSelectionDialog.Run () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
  at FSpot.Core+ImportCommand.Execute () [0x00000] 
  at FSpot.Core.Import (System.String path) [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

libgphoto2-sharp (1.0.3058.27698)
FolderExport (0.0.0.0)
FlickrExport (0.0.0.0)
PicasaWebExport (0.0.0.0)
CDExport (0.0.0.0)
SmugMugExport (0.0.0.0)
GalleryExport (0.0.0.0)
pango-sharp (2.12.0.0)
FSpot.Query (0.0.0.0)
SemWeb (0.7.1.0)
glade-sharp (2.12.0.0)
gtkhtml-sharp (3.16.0.0)
System.Transactions (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
System.Configuration (2.0.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.20.0.0)
FSpot.Utils (0.0.0.0)
gdk-sharp (2.12.0.0)
gnome-vfs-sharp (2.20.0.0)
Mono.Addins (0.3.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins.Setup (0.3.0.0)
gnome-sharp (2.20.0.0)
glib-sharp (2.12.0.0)
f-spot (0.4.3.1)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-23-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
lenny/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

---

### Post by ericeclifford on 2009-09-03
Anyone might know what this could be? :(

---

### Post by directhex on 2009-09-03
Not sure what could cause this NRE, but Mono and F-Spot in Hardy are very old - so I won't have encountered any similar issues

---

### Post by ericeclifford on 2009-09-04
Well it is happening on the custom live cd that I am making, but on my other version it did not have this problem, and it is not due to an update because I have my own repository that have not been updated for awhile.

---

### Post by carniola on 2009-09-14
I'm getting the exact same error when trying to import photos, except I'm using Intrepid. Didn't have this problem before.

---

