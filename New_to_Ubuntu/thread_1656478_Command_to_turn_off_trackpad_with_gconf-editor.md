---
title: "Command to turn off trackpad with gconf-editor?"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by gregalynch on 2010-12-30
I'm able to turn off the bothersome touchpad on my new laptop using gconf-editor, and I'd really like to make a button for my toolbar that I can just click on to do it automatically (rather than having to go through all the clicks of doing it on gconf.  

The way you do it with the GUI is by opening the folders: desktop -> gnome -> peripherals -> touchpad -- this brings up a series of check boxes, one of which is touchpad_enabled.  I would love to be able to launch gconf-editor and check/uncheck this box with the click of a button, but I don't know enough to know what the command would be to do this so that I can make a custom launcher to do it.

Also, it would need to be the case that, regardless of the value when I turn it off, that the touchpad would turn back on again whenever the OS stars up - so that I don't end up in a situation where I turn on my computer and can't move the cursor up to the button to turn the trackpad back on.

Anyone with more smarts than me know how to do this?  I'd be really grateful.

---

### Post by Brandon Williams on 2010-12-31
Based on the path you specified for gconf-editor, the command line for gconftool-2 would look something like this:```
gconftool-2 --set /desktop/gnome/peripherals/touchpad/touchpad_enabled --type=bool false
```
If you want your button to toggle the setting when clicked, then this script should do it:```
#!/bin/sh
NOW=$(gconftool-2 --get /desktop/gnome/peripherals/touchpad/touchpad_enabled)
if [ "$NOW" = true ]; then
    NEW=false
else
    NEW=true
fi
gconftool-2 --set /desktop/gnome/peripherals/touchpad/touchpad_enabled --type=bool $NEW
```

---

### Post by gregalynch on 2011-01-01
that's works - thanks!  it also gave me an opportunity to learn about how to execute scripts.

one other question - it is possible to change something so that the touchpad would automatically be turned back on upon startup?  I don't want to forget to turn the touchpad on then powerup and have no control over the cursor.

---

### Post by Brandon Williams on 2011-01-02
I would define a custom keystroke that will run your script so that you can re-enable the touchpad after login with a simple keystroke.

---

### Post by gregalynch on 2011-01-02
> **Brandon Williams said:**
> I would define a custom keystroke that will run your script so that you can re-enable the touchpad after login with a simple keystroke.

Right - I thought of that a little after I posted this.  I did that and now everything works great.  Thanks again!

---

