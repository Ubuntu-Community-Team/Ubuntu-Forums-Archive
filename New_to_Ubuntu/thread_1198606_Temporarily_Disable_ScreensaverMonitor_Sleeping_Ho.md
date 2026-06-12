---
title: "Temporarily Disable Screensaver/Monitor Sleeping Hotspot"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by caue.rego on 2009-06-27
Like when I run any video, neither the screensaver will go up or monitor save energy, and just like on the mac, I want to be able to do that (temporarily disable screen to fading away in anyway) through moving the mouse to the corner of the screen, or some other simple alike way.

With compiz command plugin I can run a command line when the mouse hits the spot, but none when the mouse leaves it. Still maybe all I need here is a script using the following:

```

#To disable the screensaver:
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false

#To disable monitor sleeping:
gconftool-2 -s /apps/gnome-power-manager/ac_sleep_display --type=int 0

```

I honestly haven't tried or did much research on this yet. But I doubt it will work because how would it be re-enabled?

---

