---
title: "power management scripting or command help"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-03-14
i have my power management set to put the display to sleep after 40 minutes. need a command to disable and enable this without changing the settings in power management. need to disable for watching movies on the net. below are examples of what i use to do the samething with my screensaver

gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false

gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool true

the first is to disable and the second to enable

tks

---

### Post by unutbu on 2009-03-14
Perhaps try this:
```

xset -dpms    # disables DPMS (Energy Star) features.
xset +dpms    # enables DPMS (Energy Star) features.
xset q        # view your current xset settings

```

---

### Post by sdennie on 2009-03-14
Try: [ HOWTO: Disable screen saver while Flash is running]("http://ubuntuforums.org/showthread.php?t=1090393")

---

### Post by unutbu on 2009-03-14
Oh... now I get what was being asked! :redface:
LOL, thanks sdennie.

---

### Post by rburkartjo on 2009-03-15
tks unu that is what i was looking for works great. even though i was disabling the screensaver with what i posted before the power management was still active and my display would shutdown in 40 min which is what i had it set to do

---

