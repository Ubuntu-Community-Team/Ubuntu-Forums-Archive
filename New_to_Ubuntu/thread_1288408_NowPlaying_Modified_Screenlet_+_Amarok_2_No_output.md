---
title: "NowPlaying Modified Screenlet + Amarok 2: No output"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Matuku on 2009-10-11
I'm trying to use the modified Nowplaying screenlet (with Amarok support) but it's not working; no song info, no button responses, nothing.

The screenlet is from:
[http://gtk-apps.org/content/show.php/Nowplaying+Screenlet+modified?content=113532](http://gtk-apps.org/content/show.php/Nowplaying+Screenlet+modified?content=113532)

And the terminal output when I run the .py file is:
```

python /home/james/.screenlets/NowPlaying/NowPlayingScreenlet.py 
CachingBackend: Loading instances from cache
CachingBackend: Loading <NowPlaying1>
Found a running session of NowPlaying, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.NowPlaying was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.james.running
Loading instances in: /home/james/.config/Screenlets/NowPlaying/default/
File: NowPlaying1.ini
/home/james/.config/Screenlets/NowPlaying/default/NowPlaying1
No module named pydcop
Could not load Amarok1API API
LOAD NEW THEME: default
FOUND: /home/james/.screenlets/NowPlaying/themes/default
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Set options in NowPlayingScreenlet
LOAD NEW THEME: default
FOUND: /home/james/.screenlets/NowPlaying/themes/default
amarok 2
Restored instances from session 'default' ...
Found a player Amarok2API
Setting callbacks
Registering Callback
Found a player Amarok1nodcopAPI
Setting callbacks
OK

```

The screenlet just sits there with "Amarok1nodcop" on it; it still seems to be trying to use that even though I've selected Amarok 2 in the player option.

---

