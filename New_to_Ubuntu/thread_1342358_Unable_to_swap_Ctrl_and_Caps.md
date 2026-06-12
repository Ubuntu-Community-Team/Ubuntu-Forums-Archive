---
title: "Unable to swap Ctrl and Caps"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by irate.turtle on 2009-11-30
Following is the contents of my .Xmodmap
```
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L

```

I also tried "System > Preferences > Keyboard > Layouts > Layout Options" and chose "swap Ctrl and Caps Lock"

However neither seem to swap these keys within Gnome environment.

The keys do swap within [_**awesome**_]("http://awesome.naquadah.org/")

```
$ uname -a
Linux xxxxx 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```

---

