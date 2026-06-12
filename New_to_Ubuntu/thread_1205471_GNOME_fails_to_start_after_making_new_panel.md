---
title: "GNOME fails to start after making new panel"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-07-06
I recently added a new panel on the bottom of my desktop to hold shortcuts, kinda like a dock but for low memory. Well, I figured I could have applications on one dock to the left on the bottom of the screen, and another for folders on the right bottom of the screen.

As soon as I made the new dock, I lost functionality of the computer. Couldn't ctrl-alt-backspace, force quit, nothin. So I restarted the computer through a hard shut down and the new panel's still there. This  renders the computer unusable just like before the shutdown.

When I restart the pc, the panels load (but nothing on them loads, no applets, clock, transparency settings). I can't run any programs through alt-f2, the wallpaper displays and the wireless network password dialogue displays.

What should I do in this situation? I'd like to remove the panel but cannot do it through the conventional way. Is there a terminal way to remove panels?

---

### Post by kpkeerthi on 2009-07-06
What dock? Do you remember?

---

### Post by nothingspecial on 2009-07-06
A couple of things I would try.

First restart, click sessions at the login screen and try to log in to a failsafe gnome session. You could see if you can remove it from there.

If not then

```
killall gnome-panel
```

Then navigate to ~/.config/gnome/gnome-panel

and delete anything in there then restart gnome-panel.

If all else fails you could try
```

sudo apt-get remove --purge gnome-panel
```

Then reinstall it

```
sudo apt-get install gnome-panel
```

---

### Post by mattbutsko on 2009-07-07
It was a bottom panel. labeled as "panel_0".

Failsafe GNOME didn't work. I can't try the code because I can't use anything at all.

I ended up formatting the computer last night, luckily I just got this one 5 days ago so I didn't lose much.

---

