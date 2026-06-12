---
title: "Questions with Defaults and Totem"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-09-08
Hi I was wondering where is the config file for the auto play inputs(like for movie/dvd/audio)

Also on totem, it starts my DVD in spanish every time, and the next and back chapter selectors do not work at all.

Anyone have any fixes or workarounds for the things mention above,

Thanks in advance.

---

### Post by mc4man on 2009-09-08
> I was wondering where is the config file for the auto play inputs(like for movie/dvd/audio)

That and several other useful settings are in file management which is a menu item in system -> preferences that by default isn't shown

You can enable it in many ways
r. click on applications -> edit menus
or in a terminal
```
alacarte
```

or go directly with either
nautilus -> edit -> preferences

or in a terminal
```
nautilus-file-management-properties
```

(they should just enable file management in the first place and stop treating new users like they're potential idiots

As far as your totem movie player issues with dvd's, the best fix is to use another player, totem-gstreamer isn't well suited to dvd playback

totem-xine will work quite well if you wish to use  a totem player

```
sudo apt-get install totem-xine
```

If after installing it doesn't show up in your Applications menu then run alacarte and enable it in your Sound & Video menu  - Movie Player (Xine)

---

### Post by ericeclifford on 2009-09-08
Thank you man,

I am uninstalling the gstreamer right now and installing the xine again, for some reason it still comes up with gstreamer.works great, the xine-totem player works great with DVD's, better then VLC or Mplayer IMO.

---

