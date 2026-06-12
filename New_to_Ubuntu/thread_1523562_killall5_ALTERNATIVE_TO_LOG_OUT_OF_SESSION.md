---
title: "killall5 ALTERNATIVE TO LOG OUT OF SESSION?"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by Isaacgallegos on 2010-07-03
So I can go to ctrl+alt+F1 and have a terminal. 
If I have to close my GUI session (ctrl+alt+F7) or restart it, killall5 is the only possible way from the terminal, aka ctrl+alt+F1, to exit the GUI session, with out rebooting!?!?

---

### Post by Ocxic on 2010-07-03
ctrl-alt-backspace used to restart X.org, I think it has been disabled in the new releases, tho i do believe you can re-enable it.

check here for info: [http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html)

---

### Post by Isaacgallegos on 2010-07-04
So there is no terminal command (not to be confused with the gnome terminal), other than $ killall5?

---

### Post by Isaacgallegos on 2010-07-04
Let me ask this another way, 

How can I use the $ gnome-session-save --kill--silent command outside of the gnome desktop? If I'm not using the gnome terminal, how can I close the running gnome session?

---

### Post by Isaacgallegos on 2010-07-08
bump?

---

### Post by marshmallow1304 on 2010-07-08
```
sudo service gdm stop
```

---

### Post by Isaacgallegos on 2010-07-09
Thank you thank you thank you!!!!!!!!!!!!!!!!!
You just saved my life!

---

