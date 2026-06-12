---
title: "keyboard shortcuts with compiz ???"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by RyanVanDiemen on 2009-12-15
I like switching between desktops in KDE by Ctrl+Fn (n=1,2,3...). I`d like to use them in gnome but if I have the compiz turned on it takes over the desktop and ignores the shortcuts I set in "keyboard shortcuts". Does anyone know how to tell compiz to use Ctrl+Fn keys for switching between desktops?

---

### Post by marshmallow1304 on 2009-12-15
```
sudo apt-get install compizconfig-settings-manager
```

If you have the Desktop Cube enabled, you'll want to change the bindings on Rotate Cube.  Look under "Rotate to cube face".  I don't know if this is possible with the regular Desktop Wall.

---

### Post by RyanVanDiemen on 2009-12-16
Thanks marshmallow, but how do I tell it to change the workspaces by Ctrl+Fn keys?

---

