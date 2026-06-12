---
title: "What Do these errors Mean?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Howard Roark on 2009-11-03
?????@?????-desktop:~$ Rhythmbox
No command 'Rhythmbox' found, did you mean:
 Command 'rhythmbox' from package 'rhythmbox' (main)
Rhythmbox: command not found
linda@linda-desktop:~$ rhythmbox

** (rhythmbox:1919): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:1919): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect


?????@?????-desktop:~$ banshee
[Info  21:51:30.599] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, i486) @ 2009-10-19 14:46:07 UTC]
[Info  21:51:34.316] Querying MusicBrainz for Disc Release (5NiqIxSWilgz.i6l4IOKm9JVq4I-)
[Info  21:51:34.425] All services are started 3.128352s
[Info  21:51:36.692] Query finished (success: True, 2.375397 seconds)
[Info  21:51:36.989] nereid Client Started
[Warn  21:51:37.700] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at Hal.IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 
[Warn  21:51:38.036] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at Hal.IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 
[Warn  21:51:38.358] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at Hal.IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 
[Warn  21:51:38.685] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at Hal.IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000]

---

### Post by jimmy the saint on 2009-11-03
If the programs run fine, just ignore all that crap.  There are several programs that I have yet to see run without kicking out a few warnings.  Rhythmbox has NEVER opened from a terminal for me without kicking out at least a dozen.  To my mind, they are irrelevant unless the program is broken in some way for you.

---

### Post by LarsW_Tierp on 2009-11-03
You should not have to worry about the messages. My Rhytmbox works just fine and is putting out these warnings when stared from command line.

---

