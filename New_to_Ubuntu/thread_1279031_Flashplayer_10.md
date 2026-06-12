---
title: "Flashplayer 10"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-09-30
Okay, so a website told me I don't have the latest flash player.  I went to the Adobe download page and tried to download it.  The Installation got hung up because I didn't know what to put in at one point.  So I checked on here and found out about gnash and the flashplayer plugin.  I tried to uninstall gnash and was told it wasn't installed.  I tried the apt get for the flshplayer plugin and was told it would not install.   What da heck?

---

### Post by achase79 on 2009-09-30
you can just download the deb from adobe then use an archive manager to open and extract the flashplayer.so file to the /usr/share/mozilla/plugins directory.

---

### Post by rajeev1204 on 2009-09-30
> **Gulfvet91 said:**
> Okay, so a website told me I don't have the latest flash player.  I went to the Adobe download page and tried to download it.  The Installation got hung up because I didn't know what to put in at one point.  So I checked on here and found out about gnash and the flashplayer plugin.  I tried to uninstall gnash and was told it wasn't installed.  I tried the apt get for the flshplayer plugin and was told it would not install.   What da heck?


In a  terminal ...

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by 3rdalbum on 2009-09-30
Not enough information; what error message did it give when you tried to install the "flashplugin-nonfree" package?

That's the recommended, easiest way to install Flash Player.

---

