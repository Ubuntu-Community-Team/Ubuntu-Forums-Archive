---
title: "Too many toolbar icons"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by wooly on 2009-01-23
I was working too late & dozing off. Seems that I added an icon to the toolbar over 100 times.
I've tried right-clicking and choosing "Remove from Panel" over 100 times but there are too many of them!
Is there a tool bar configuration file that I can edit? Thanks for any help you can give!

---

### Post by keishia.tee on 2009-01-23
lol oops
you could delete the panel (right click) and add a new one to replace it...

---

### Post by Temposs on 2009-01-23
Off hand I would say right click the panel and choose "Delete This Panel"

Then add a new panel and put the stuff on there that you want.

---

### Post by wooly on 2009-01-23
Thanks, but there's no open space to right-click on, 
and the System/Places/Applications icons are no longer visible.

Anyone know the name of the configuration file for the toolbar?

---

### Post by wooly on 2009-01-23
> **wooly said:**
> I was working too late & dozing off. Seems that I added an icon to the toolbar over 100 times.
I've tried right-clicking and choosing "Remove from Panel" over 100 times but there are too many of them!
Is there a tool bar configuration file that I can edit? Thanks for any help you can give!
OK, I finally right-clicked enough of the icons to get rid of them.
Never did find the toolbar config file.

---

### Post by drs305 on 2009-01-23
> **wooly said:**
> Thanks, but there's no open space to right-click on, 
and the System/Places/Applications icons are no longer visible.


In that case, to restore the original top & bottom default panels:
```

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

```

Once you have restored the panel with your shortcuts and personal modifications, you can save the panel settings (example to file ~/Desktop/panels):
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```

To restore saved panel settings and refresh the panel (example from file ~/Desktop/panels) :
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```
Sorry you weren't aware of this method to save your panel settings before the mishap.  ;-)

---

### Post by wooly on 2009-01-23
Thanks- that's what I was looking for. I'm going to save my settings right now!

> **drs305 said:**
> In that case, to restore the original top & bottom default panels:
```

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

```

Once you have restored the panel with your shortcuts and personal modifications, you can save the panel settings (example to file ~/Desktop/panels):
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```

To restore saved panel settings and refresh the panel (example from file ~/Desktop/panels) :
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```
Sorry you weren't aware of this method to save your panel settings before the mishap.  ;-)

---

