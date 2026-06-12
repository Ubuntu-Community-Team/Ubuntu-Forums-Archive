---
title: "Changing shelf text color"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by snip3r8 on 2011-08-08
The writing in my kde shelf widget is black and my theme is very dark,how can i change the color of the writing without changing my theme.

---

### Post by raja.genupula on 2011-08-08
have you seen in settings of that , i am not  using that . but give a try , have a look in settings

---

### Post by snip3r8 on 2011-08-09
The widgets themselves don't have any color settings at all

---

### Post by snip3r8 on 2011-08-10
The shelf is part of lancelot so if i could just change the text color of that it would help.

---

### Post by snip3r8 on 2011-08-10
Ok, I solved the problem 

to change colors in lancelot edit the following file:
/usr/share/kde4/apps/desktoptheme/default/lancelot/theme.config

or just to get lighter text ,copy from oxygen:
```
sudo cp /usr/share/kde4/apps/desktoptheme/oxygen/lancelot/theme.config /usr/share/kde4/apps/desktoptheme/default/lancelot/theme.config
```

---

