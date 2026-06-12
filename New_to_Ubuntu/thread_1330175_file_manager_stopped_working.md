---
title: "file manager stopped working"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by quercusrobur on 2009-11-18
Hi can anybody advise - I'm using Ubuntu 9.10. For some reason the file manager has stopped working. I was editing some files with Inkscape which crashed. I used the 'force quit' applet to exit this application. After this double clicking on a desktop icon no longer worked, nor could I explore any folders using the 'Places' menu. Have shut down and restarted the laptop twice but no help. When shutting down I got the message that 'File Manager is not working'. Any advice gratefully accepted! Thanks

---

### Post by prshah on 2009-11-18
> **quercusrobur said:**
> I got the message that 'File Manager is not working'. 

Can you try launching the file manager from a terminal (Applications-Accessories-Terminal)? 

If you are using gnome, give the command ```
nautilus
```
if you are using KDE (kubuntu), give the command```
dolphin
```
If you are using xfce(Xubuntu), give the command```
thunar
```

Please post back error messages; this can give a clue as to what is wrong and how to fix it.

---

### Post by quercusrobur on 2009-11-18
typed 'nautilus' into a terminal and got this output;

graham@graham-laptop:~$ nautilus

(nautilus:2473): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

---

### Post by quercusrobur on 2009-11-18
Finally worked out that a corrupt file on the desktop was causing the problem, but couldn't delete it as everytime I went anywhere near it Nautilus would freeze - eventually dealt with it by installing Thunar and using that to delete it - everything seems to be working fine now!!

---

