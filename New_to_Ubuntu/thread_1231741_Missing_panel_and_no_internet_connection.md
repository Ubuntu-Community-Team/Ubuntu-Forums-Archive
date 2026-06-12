---
title: "Missing panel and no internet connection"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Seburn88 on 2009-08-04
Okay, I'm a novice at everything ubuntu, and I apologize in advance.

The first problem that I was trying to address today was the fact that my panel has completely disappeared.  I have been visiting various forums and following their instructions but nothing has worked thus far (and I really don't know what I did and how it was supposed to fix the problem!).

Then I realized that my wireless network info has been changed since this problem started.  I think I could have reconfigured the settings when I had access to the panel but now I really have no idea what to do.  I think this problem may be blocking my ability to reinstall/update gnome.

So question number one is really how to be able to change my wireless settings (without using the panel) so that I can enter my new network info!

Any help would be very much appreciated!

---

### Post by nothingspecial on 2009-08-05
[COLOR="Red"][SIZE="3"]Do not type the second line in the second code box wrong, if you are unsure please copy and paste[/SIZE][/COLOR]

Try typing

```
gnome-panel
```

If that doesn`t work try

```
gconftool –recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

If non of that works try 

```
nm-applet
```

---

