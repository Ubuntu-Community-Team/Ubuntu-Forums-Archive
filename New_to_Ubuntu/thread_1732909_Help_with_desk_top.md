---
title: "Help with desk top"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by famous3warriors on 2011-04-18
I have ubuntu 11.04 and I was messing around with compiz settings I accidentally resolved unitu plug in and now my desk top is plain.  Everything is hidden I would like to know how to put every thing back to normal.  I do not see the menu bar no apps in the side like it used to be.  Thanks in advance for your help.

---

### Post by r-senior on 2011-04-18
Try Ctrl-Alt-F1 to get to a virtual terminal, then

```

unity --reset
sudo service gdm restart

```

That should reset all the settings back to default and get you back to the login screen.

---

### Post by famous3warriors on 2011-04-18
R senior thanks for help tried that but didn't work hit ctrl alt f1 and my screen went blank and that's it

---

### Post by beew on 2011-04-18
That happened to me before. Right click anywhere to create a new folder, open the folder to access file manager, then go to /usr/share/applications, from there you can start ccms and restart unity.

Since you lose the desktop without Unity there should be some safeguard against accidental disabling Unity.

---

### Post by famous3warriors on 2011-04-19
Thanks beew it worked perfect I really do appreciate it.

---

