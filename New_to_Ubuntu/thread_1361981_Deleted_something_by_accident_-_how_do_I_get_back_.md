---
title: "Deleted something by accident - how do I get back the display of windows I have open?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by anewguy on 2009-12-22
Okay, know this is stupid.  I reinstalled everything (did something REALLY stupid - modem was bad but I thought it was my install!) for default Ubuntu 9.10 install.  Then after adding some other things I needed and the updates, I added in the KDE desktop and apps.  Today I did *something* (not sure what - I remember something about "remove from panel" but I *thought* I clicked cancel) that resulted in KDE not showing the open windows in the bottom "task bar" anymore.  Can someone tell me how to get that back?

Thanks in advance!
Dave :)

---

### Post by lkraemer on 2009-12-23
Dave,
I haven't tried this in KDE but it should work the same as in Gnome.

Since you deleted the Workspace Switcher Preferences, or at least that
is what I believe you have deleted.....

Just move your cursor over an open space in the lower toolbar and then
Right Click, then select ADD TO PANEL.  Scroll down to WORKSPACE SWITCHER
and add it back to the Panel.

You should be back in business.

lk

---

### Post by IsstanarLW on 2009-12-23
Right click panel, panel options/add widgets. search for task in widgets display

---

### Post by llawwehttam on 2009-12-23
in gnome you can do a 
gconftool-2 --recursive-unset 
to restore default settings. 
Not sure how to do this in kde tho

---

### Post by anewguy on 2009-12-23
Thanks for the replies, everyone!  Indeed, in this case I needed to click on the bar, click add widgets, and select Task Manager as lkraemer and IsstanarLW eluded to.  Worked great!

Thanks again!
Dave :)

---

