---
title: "keyboard doesn't work"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by DavidVader on 2010-09-17
I don't know what actually happened, but now when I boot my Ubuntu it lets me login and afterwards the keyboard doesn't respond at all. Is there any way to solve this?

Thanks in advance.

---

### Post by ubunterooster on 2010-09-17
Okay, it interests me how you are typing this (same keyboard, but another OS; or another keyboard, same OS)

---

### Post by DavidVader on 2010-09-18
Same keyboard, another OS.

---

### Post by ubunterooster on 2010-09-18
:(

This is a gnome problem from my experience. If you have XFCE / LXDE on the same partition as the nonworking gnome one the keyboard will work.

I had to delete all gnome configuration files in order to get it working. Brutal, but effective.

---

### Post by scorchgeek on 2010-09-18
You might try setting the "Legacy USB Keyboard" option in your BIOS (assuming your keyboard is USB). Seems to have solved many of my odd keyboard problems in the past.

May not work at all, but it's worth a shot.

---

### Post by DavidVader on 2010-09-18
Problem solved. It was just the "Slow key" indicator that was set too high. So if you might have such a problem just go to Keyboard Preferences...and you'll find the solution at the Accessibility tab.

---

