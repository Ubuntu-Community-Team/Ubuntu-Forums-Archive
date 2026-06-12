---
title: "Gnome-do Not Working"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by suprman2020 on 2009-11-27
Gnome-do doesn't work for me anymore. When I first did a clean install of Karmic Koala, it was working. I don't remember what happened, but one day it just stopped working. Any help is appreciated. This is what it outputs when I run it in the terminal:

> 
(Do:8099): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/solomon/.recently-used.xbel', but the parser failed: Error reading file '/home/solomon/.recently-used.xbel': Is a directory.

(Do:8099): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[Error 23:53:24.700] [AbstractKeyBindingService] Failed to bind "Summon in Text Mode" to ""
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Data.SqliteClient.SqliteDataReader.GetString (Int32 i) [0x00000] 
  at Firefox.PlacesItemSource+<LoadPlaceItems>c__Iterator3.MoveNext () [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem].AddEnumerable (IEnumerable`1 enumerable) [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem]..ctor (IEnumerable`1 collection) [0x00000] 
  at System.Linq.Enumerable.ToArray[PlaceItem] (IEnumerable`1 source) [0x00000] 
  at Firefox.PlacesItemSource.UpdateItems () [0x00000] 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] .

** (Do:8099): WARNING **: Missing method Do.Platform.AbstractApplicationService::RunOnThread(Action) in assembly /usr/lib/gnome-do/Do.Platform.dll, referenced in assembly /usr/lib/gnome-do/plugins/WeatherDocklet.dll
[Error 23:53:25.440] Error in RunOnMainThread: Method not found: 'Do.Platform.AbstractApplicationService.RunOnThread'.
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Data.SqliteClient.SqliteDataReader.GetString (Int32 i) [0x00000] 
  at Firefox.PlacesItemSource+<LoadPlaceItems>c__Iterator3.MoveNext () [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem].AddEnumerable (IEnumerable`1 enumerable) [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem]..ctor (IEnumerable`1 collection) [0x00000] 
  at System.Linq.Enumerable.ToArray[PlaceItem] (IEnumerable`1 source) [0x00000] 
  at Firefox.PlacesItemSource.UpdateItems () [0x00000] 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] .
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Data.SqliteClient.SqliteDataReader.GetString (Int32 i) [0x00000] 
  at Firefox.PlacesItemSource+<LoadPlaceItems>c__Iterator3.MoveNext () [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem].AddEnumerable (IEnumerable`1 enumerable) [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem]..ctor (IEnumerable`1 collection) [0x00000] 
  at System.Linq.Enumerable.ToArray[PlaceItem] (IEnumerable`1 source) [0x00000] 
  at Firefox.PlacesItemSource.UpdateItems () [0x00000] 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] .
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Data.SqliteClient.SqliteDataReader.GetString (Int32 i) [0x00000] 
  at Firefox.PlacesItemSource+<LoadPlaceItems>c__Iterator3.MoveNext () [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem].AddEnumerable (IEnumerable`1 enumerable) [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem]..ctor (IEnumerable`1 collection) [0x00000] 
  at System.Linq.Enumerable.ToArray[PlaceItem] (IEnumerable`1 source) [0x00000] 
  at Firefox.PlacesItemSource.UpdateItems () [0x00000] 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] .
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Data.SqliteClient.SqliteDataReader.GetString (Int32 i) [0x00000] 
  at Firefox.PlacesItemSource+<LoadPlaceItems>c__Iterator3.MoveNext () [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem].AddEnumerable (IEnumerable`1 enumerable) [0x00000] 
  at System.Collections.Generic.List`1[Firefox.PlaceItem]..ctor (IEnumerable`1 collection) [0x00000] 
  at System.Linq.Enumerable.ToArray[PlaceItem] (IEnumerable`1 source) [0x00000] 
  at Firefox.PlacesItemSource.UpdateItems () [0x00000] 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] .


---

### Post by Buuntu on 2009-11-27
Type this into the terminal (as long as you don't mind losing all the configuration of gnome-do if you had any):
```
sudo apt-get purge gnome-do && sudo apt-get install gnome-do
```

**You can replace 'purge' with 'remove' in the above command if you want to keep your configuration files, but 'purge' is probably more likely to work for completely reinstalling a working package.

---

### Post by suprman2020 on 2009-11-27
> **Buuntu said:**
> Type this into the terminal (as long as you don't mind losing all the configuration of gnome-do if you had any):
```
sudo apt-get purge gnome-do && sudo apt-get install gnome-do
```

**You can replace 'purge' with 'remove' in the above command if you want to keep your configuration files, but 'purge' is probably more likely to work for completely reinstalling a working package.

Thanks. Your solution worked.

---

### Post by kendoori on 2009-11-27
I rely on the Gome-Do Docky theme and was finding that the dock stopped working and the program intermittent. It seems as though the current version has some issues with plugins, the weather one specifically. I've since turned off the weather applet and Do is stable for me. In case your reinstall doesn't work, try disabling plugins one by one (start with Weather if you are using it). I had reinstalled and it seemed to work at first, but then started not working again.

---

### Post by suprman2020 on 2009-11-27
> **kendoori said:**
> I rely on the Gome-Do Docky theme and was finding that the dock stopped working and the program intermittent. It seems as though the current version has some issues with plugins, the weather one specifically. I've since turned off the weather applet and Do is stable for me. In case your reinstall doesn't work, try disabling plugins one by one (start with Weather if you are using it). I had reinstalled and it seemed to work at first, but then started not working again.

Docky is now a program by itself so I just use that instead,but I still want to use gnome-do as my launcher. You are correct about gnome-do not working again. I will try your solution.

---

