---
title: "Restoring top panel to normal."
date: 2010-11-16
forum: New to Ubuntu
---

### Post by Jetso on 2010-11-16
On my top panel, I accidently deleted the wireless icon and battery. Is there a way to just reset the whole top panel to get them all back, because I know I deleted something else, but I forget what I deleted.

---

### Post by Jechem on 2010-11-16
in terminal run these three:

gconftool --recursive-unset /apps/panel

rm -rf ~/.gconf/apps/panel

pkill gnome-panel

---

### Post by Rex Bouwense on 2010-11-16
I believe Jechem has a solution. I think that if you right click the top panel and then left click add to panel and then Notification Area, you may also have a solution.  Try it, if it doesn't work you are not out anything.

---

### Post by Jetso on 2010-11-16
Aha, there it goes! I shall mark post as solved.

---

