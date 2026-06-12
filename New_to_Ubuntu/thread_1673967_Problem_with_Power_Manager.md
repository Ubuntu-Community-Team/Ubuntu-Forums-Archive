---
title: "Problem with Power Manager"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by gauravgupta on 2011-01-23
My laptop is having problem with power manager..
Each time i unplug my laptop from ac it goes to hibernate even if full battery.
please help i cant use it as a laptop..i always have to have it plugged.
please help!

---

### Post by ajgreeny on 2011-01-23
Try this; it can help with some laptops and netbooks which do this.

Open up gconf-editor, if it's not in the menu use Alt+F2 and type *gconf-editor* in the box.

Go to apps->gnome-power-manager->general and put a tick mark in the *use_time_for_policy* key.

If that does not help, I'm afraid I know of no other ways to overcome the problem.

---

