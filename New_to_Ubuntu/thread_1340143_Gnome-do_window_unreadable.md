---
title: "Gnome-do window unreadable"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by myotis on 2009-11-28
I have just upgraded from Jaunty to Karmic, and Gnome-do is giving me problems in that when I launch it, all I get is a multi-coloured window (looks a bit like tartan).

I tried 

sudo apt-get purge gnome-do && sudo apt-get install gnome-do

from another post, to give me a clean install but this hasn't helped.

I am on a Thinkpad T42.

Can anyone help.

I have edited this because it seems I have the same problem running system monitor, but only if I go through the System menu, if I launch from the applications menu, it is OK.

Gnome-Do is broken however I launch it.

Many thanks,

Graham

---

### Post by myotis on 2009-11-28
Mmmm, actually I find that this isn't just Gnome-do but also the systems monitor, so maybe its a broader graphics driver issue.

Graham

---

### Post by PGScooter on 2009-11-28
have you tried running gnome-do in debug mode to see what's going on?

try:
```
gnome-do --debug
```

---

### Post by myotis on 2009-11-28
> **PGScooter said:**
> have you tried running gnome-do in debug mode to see what's going on?

try:
```
gnome-do --debug
```

Thanks, the print out is below and I see I have a few errors, but not sure of the relevance.

graham@T42-laptop:~$ gnome-do --debug
WARNING: [Do.Banshee,1.0] Could not load some add-in assemblies: File '/usr/lib/banshee-1/Banshee.CollectionIndexer.dll' not found.
ERROR: Errors found in add-in '/usr/lib/gnome-do/plugins/Banshee.dll:
ERROR: The file '/usr/lib/banshee-1/Banshee.CollectionIndexer.dll' referenced in the manifest could not be found.
[Debug 16:05:21.881] [SystemService] Using org.freedesktop.DeviceKit.Power for battery information
[Info  16:05:21.892] [Services] Successfully located service of type ILogService.
[Info  16:05:21.893] [Services] Successfully located service of type IPreferencesService.
[Info  16:05:21.895] [Services] Successfully located service of type ISecurePreferencesService.
[Info  16:05:21.901] [Services] Successfully located service of type INotificationsService.
[Debug 16:05:21.908] [InterfaceManager] "Docky" interface was loaded
[Info  16:05:21.909] [Services] Successfully located service of type ILogService.
[Debug 16:05:21.909] [InterfaceManager] "Mini" interface was loaded
[Debug 16:05:21.910] [InterfaceManager] "Classic" interface was loaded
[Debug 16:05:21.911] [InterfaceManager] "Nouveau" interface was loaded
[Debug 16:05:21.912] [InterfaceManager] "Glass" interface was loaded
[Debug 16:05:21.918] [PluginManager] Loaded "SessionCommandsItemSource" from plugin.
[Debug 16:05:21.919] [PluginManager] Loaded "NotesItemSource" from plugin.
[Info  16:05:21.942] [Services] Successfully located service of type IPreferencesService.
[Info  16:05:21.942] [Services] Successfully located service of type ISecurePreferencesService.
[Info  16:05:21.949] [Services] Successfully located service of type ICoreService.
[Info  16:05:21.951] [Services] Successfully located service of type INetworkService.
[Debug 16:05:21.975] [PluginManager] Loaded "WeatherItemSource" from plugin.
[Info  16:05:21.977] [Services] Successfully located service of type AbstractApplicationService.
[Debug 16:05:21.983] [PluginManager] Loaded "InternalItemSource" from plugin.
[Debug 16:05:21.984] [PluginManager] Loaded "ItemSourceItemSource" from plugin.
[Debug 16:05:21.986] [PluginManager] Loaded "PlacesItemSource" from plugin.
[Debug 16:05:21.988] [PluginManager] Loaded "ApplicationItemSource" from plugin.
[Debug 16:05:21.988] [PluginManager] Loaded "GNOMESpecialLocationsItemSource" from plugin.
[Debug 16:05:21.992] [PluginManager] Loaded "ProfileItemSource" from plugin.
[Debug 16:05:21.993] [PluginManager] Loaded "ScreenshotItemSource" from plugin.
[Debug 16:05:22.008] [PluginManager] Loaded "ScreenItemSource" from plugin.

(Do:2922): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[Info  16:05:22.069] [Services] Successfully located service of type PathsService.
[Debug 16:05:22.069] [PluginManager] Loaded "WindowItemSource" from plugin.
[Debug 16:05:22.086] [PluginManager] Loaded "EmailAction" from plugin.
[Debug 16:05:22.086] [PluginManager] Loaded "OpenAction" from plugin.
[Debug 16:05:22.094] [PluginManager] Loaded "OpenUrlAction" from plugin.
[Debug 16:05:22.095] [PluginManager] Loaded "OpenWithAction" from plugin.
[Debug 16:05:22.095] [PluginManager] Loaded "RevealAction" from plugin.
[Debug 16:05:22.095] [PluginManager] Loaded "RunAction" from plugin.
[Debug 16:05:22.096] [PluginManager] Loaded "OpenSearchAction" from plugin.
[Debug 16:05:22.097] [PluginManager] Loaded "PastebinAction" from plugin.
[Debug 16:05:22.097] [PluginManager] Loaded "NewNoteAction" from plugin.
[Debug 16:05:22.097] [PluginManager] Loaded "SearchNotesAction" from plugin.
[Debug 16:05:22.099] [PluginManager] Loaded "DefineAction" from plugin.
[Debug 16:05:22.099] [PluginManager] Loaded "CopyToClipboardAction" from plugin.
[Debug 16:05:22.100] [PluginManager] Loaded "MakeUrlTinyAction" from plugin.
[Debug 16:05:22.100] [PluginManager] Loaded "RunInTerminalAction" from plugin.
[Debug 16:05:22.100] [PluginManager] Loaded "OpenTerminalHereAction" from plugin.
[Debug 16:05:22.101] [PluginManager] Loaded "GoogleCalculatorAction" from plugin.
[Debug 16:05:22.101] [PluginManager] Loaded "TakeScreenshotAction" from plugin.
[Debug 16:05:22.102] [PluginManager] Loaded "WindowMinimizeAction" from plugin.
[Debug 16:05:22.102] [PluginManager] Loaded "WindowMaximizeAction" from plugin.
[Debug 16:05:22.102] [PluginManager] Loaded "WindowCloseAction" from plugin.
[Debug 16:05:22.116] [PluginManager] Loaded "WindowFocusAction" from plugin.
[Debug 16:05:22.116] [PluginManager] Loaded "WindowMoveAction" from plugin.
[Debug 16:05:22.117] [PluginManager] Loaded "ScreenTileAction" from plugin.
[Debug 16:05:22.117] [PluginManager] Loaded "ScreenCascadeAction" from plugin.
[Debug 16:05:22.117] [PluginManager] Loaded "ScreenRestoreAction" from plugin.
[Debug 16:05:22.117] [PluginManager] Loaded "ScreenSwapAction" from plugin.
[Debug 16:05:22.117] [PluginManager] Loaded "ShowDesktopAction" from plugin.
[Info  16:05:22.119] [Services] Successfully located service of type AbstractSystemService.
[Debug 16:05:22.123] [SystemService] No other application instance detected. Continue startup.
[Debug 16:05:22.169] [Controller] Setting theme Docky
[Info  16:05:22.410] [UniverseManager] Reloading universe...
[Debug 16:05:22.411] [UniverseManager] Reloading actions...
[Debug 16:05:22.422] [UniverseManager] Reloading item source "GNOME Session Commands"...
[Debug 16:05:22.424] [UniverseManager] Reloading item source "Tomboy Notes"...
Could not locate Tomboy on D-Bus. Perhaps it's not running?
[Debug 16:05:22.479] [UniverseManager] Reloading item source "Weather Commands"...
[Debug 16:05:22.480] [UniverseManager] Reloading item source "Internal GNOME Do Items"...
[Debug 16:05:22.481] [UniverseManager] Reloading item source "GNOME Do Item Sources"...
[Debug 16:05:22.525] [UniverseManager] Reloading item source "Firefox Places"...
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: Object reference not set to an instance of an object.
[Debug 16:05:22.668] [UniverseManager] Reloading item source "Applications"...
[Debug 16:05:23.276] [UniverseManager] Reloading item source "GNOME Special Locations"...
[Debug 16:05:23.289] [UniverseManager] Reloading item source "GNOME Terminal Profiles"...
[Debug 16:05:23.303] [UniverseManager] Reloading item source "GNOME Screenshot Items"...
[Debug 16:05:23.308] [UniverseManager] Reloading item source "Window Screen Items"...
[Debug 16:05:23.309] [UniverseManager] Reloading item source "Generic Window Items"...
[Info  16:05:23.309] [UniverseManager] Universe contains 443 items.
[Info  16:05:23.321] [AbstractWeatherSource] Weather Underground: Reloading weather data
[Debug 16:05:23.339] [AbstractWeatherSource] Weather Underground: Fetching XML file 'http://api.wunderground.com/auto/wui/geo/WXCurrentObXML/index.xml?query=50014'
[Debug 16:05:29.143] [AbstractWeatherSource] Weather Underground: Fetching XML file 'http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=50014'

---

### Post by myotis on 2009-11-30
Well, this is sort of solved, in that switching on Visual effects to normal has allowed both Gnome-Do and system monitor to display.

But as, this is a relatively slow machine I had this switched off with Jaunty and Gnome-Do worked fine.

Graham

---

### Post by bigsuccess on 2009-11-30
Were you using a different theme than Docky in Jaunty?

I believe gnome-do effectively won't run in the Docky theme without compositing on. If that's what is causing this then you will be able to run it in a theme other than Docky.

might not be it...

---

### Post by myotis on 2009-11-30
> **bigsuccess said:**
> Were you using a different theme than Docky in Jaunty?

Yes, I was using the classic theme in Jaunty, and the theme choice box was greyed out after my upgrade to Karmic. BUT now you mention it, the greyed out default was Docky. I assumed that the default would have been classic.

Now that I have switched the visual effects on, the box is no longer greyed out and I can select the classic theme.

But I think this may well have been the root of the problem.

Thanks,

Graham

---

