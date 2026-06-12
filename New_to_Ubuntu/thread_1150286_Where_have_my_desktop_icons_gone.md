---
title: "Where have my desktop icons gone?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by lesliek on 2009-05-05
I just upgraded from v 8.04 to v 8.10.

Formerly, I had icons on my desktop for the computer, my home directory and the garbage bin. They're not there anymore.

I opened gconf-editor and navigated to nautilus, desktop. The boxes for the relevant icons ARE already ticked.

How do I get the icons back?

---

### Post by drs305 on 2009-05-05
Do you have *anything* showing on the desktop. If it's completely empty, you can go back into gconf-editor. Instead of nautilus/desktop, look at /nautilus/preferences and make sure "show_desktop" is enabled. This is sort of a "master" switch that controls everything else. Sometimes users turn this switch off so they can use wallpapers in compiz.

---

### Post by lesliek on 2009-05-06
Thanks for replying.

No, I don't have anything showing on my desktop. However, when I went to nautilus, preferences, "show desktop" WAS ticked already. So, though that's ticked and the desktop options for showing the icons for the computer, my home directory and the garbage bin (and for any mounted volumes) are also ticked, I still can't see them.

If you have any further suggestions, I'd be grateful.

Thanks again.

---

### Post by drs305 on 2009-05-06
Is compiz's wallpaper feature turned on. If you don't know, the simplest thing would be to turn compiz off with this command and see if you get your Desktop back. If you do, leave compiz off or use compiz but make sure the wallpaper feature is not selected.
```

metacity --replace  # turns off compiz, turns on metacity
compiz --replace  # turns off metacity, turns on compiz

```

In addition to the user, you might try making sure root's desktop is also turned on. They both have to be turned *off* to get compiz's wallpaper to work. In theory, root's settings should not interfere with your own, but I'd try turning both your and root's desktops back on anyway:

```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
sudo gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
[CODE]

If you still can't recover the Desktop, install gtweakui.
[CODE]sudo apt-get install gtweakui
```
Then: System >  Preferences > "gtweakui -Nautilus", tick/untick "Use nautilus to draw desktop"

---

### Post by lesliek on 2009-05-06
I took all those steps and rebooted. Still no icons.

If this is the worst adverse side effect of the upgrade, I can live with it, but it is annoying.

If you have any more suggestions, I'll happily give them a go.

Thanks again.

OK: Just found this: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/303023](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/303023)

So I'm not alone (though that's small comfort). I notice that someone said that the problem went away in v 9.04. My whole reason for upgrading to 8.10 was so that I could then upgrade to 9.04, but when I tried that, I was warned against it because of the absence of an up-to-date video driver for my hardware! I'm stuck in no-man's-land.

---

