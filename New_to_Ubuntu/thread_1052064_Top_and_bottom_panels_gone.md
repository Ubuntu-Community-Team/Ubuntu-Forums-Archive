---
title: "Top and bottom panels gone"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by pzs on 2009-01-27
I crashed by machine (it hung completely - quite rare) opening up lots of audio windows in Firefox (don't ask). When I rebooted, I didn't have panels at the top and bottom. I still have a .gnome2 directory and my hotkeys and media keys still seem to work, but no panels, no menus and no notification apps.

Another thing I did that may have caused these problems besides the crash was that I uninstalled Evolution. Normally, I wouldn't uninstall and application I don't use, but Evolution offends me so I removed it along with about a dozen packages that came with it. Perhaps this did some damage? I've tried reinstalling Evolution, but that hasn't made any difference - maybe it didn't reinstall all the dependents somewhere?

Does apt have a log of packages recently added/removed? I could restore all of them and see if that fixes it.

---

### Post by RomeReactor on 2009-01-27
Hi. To restore all the packages in a default Ubuntu installation, try:
```
sudo aptitude install ubuntu-desktop
```

However, you could also try this to recover the panels:
```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

---

### Post by pzs on 2009-01-27
The first option worked. Somewhere, I had actually removed gnome panel and gnome apps. I'll check the removelist more carefully next time.

I also discovered that you can autocomplete on apt-get install, which is very useful.

---

