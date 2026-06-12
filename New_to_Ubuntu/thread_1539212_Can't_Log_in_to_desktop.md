---
title: "Can't Log in to desktop"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Demrtnz on 2010-07-26
After i sign in with my user name and password, all the will load is the terminal in the upper left corner. it's also white instead of the usual black background. this also happens in graphic safe mode. i also tried

 

```
-choose recovery mode at grub
-drop to a root prompt
-type  " telinit 3 " and login
-then type " xinit "
-when xinit starts type: " metacity & " - for ubuntu OR " compiz & " - if you have it OR flux/openbox & - if you have it OR " fvwm & " - for xubuntu
-then type " gnome-panel " & -for ubuntu OR " xfce4-panel & " -for xubuntu
-lastly type " nm-applet & " -for networking
```i can force the panes and network to boot but i don't know how or what i need to do to fix the problem. any ideas?

---

### Post by -kg- on 2010-07-26
Which version of Ubuntu did you install?  Did you by any chance install the Server version?  If so, the Server version doesn't come with a desktop environment.  You'll have to install one if you want one.

---

### Post by Demrtnz on 2010-07-26
i installed the desktop verison. i went from 8.04 and upgraded to 10.04 from an alt. install cd since that was the only way i could install ubuntu/ upgrade. after i upgraded all was fine the first log in. then after i installed my nvidia video card with the hardware search under admin. and rebooted the computer, ubuntu would only show the wallpaper and the terminal.

---

