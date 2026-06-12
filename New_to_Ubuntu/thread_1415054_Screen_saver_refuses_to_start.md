---
title: "Screen saver refuses to start"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-24
OS: Ubuntu 9.10    Settings: Screen saver "Floating Ubuntus" set to fire at 5 minutes of inactivity.  Visual effects = None.  Pier systems:  6 other computers, identical hardware, identical OS, set up identical way, all updates applied up to today's date, all fire the same screen saver at 5 minutes of inactivity.

I have one "rogue" computer that refuses to fire the screen saver after 5 minutes of inactivity.  It sits there all night with the "brown sand dunes" standard background.  I have tried putting the cursor in different locations, just in case it's like the MS Windows "place cursor over task bar and the screen saver will not fire" situation.  Makes no difference.

How can I force the screen saver to start after 5 minutes of inactivity.

---

### Post by ubudog on 2010-02-25
Make sure it is running.  Open a terminal and type: ```
gnome-screensaver
``` and press enter.  Then press CTL>ALT>L and it should come on.

---

### Post by RedOctober on 2010-02-26
I checked using gnome-screensaver (thanks for that), and it warned me that it was already running.  I was able to fix it by doing the following:  (I don't have a copy of Ubuntu running in front of me so I have to guess at the captions...

1) Uncheck the "Automatically start screen saver on inactivity" box
2) Reboot
3) Change the time out limit from 5 minutes to 6 minutes
4) Reboot
5) Check the "Automatically start screen saver on inactivity"

Works now.

---

