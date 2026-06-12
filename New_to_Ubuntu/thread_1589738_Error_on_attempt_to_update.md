---
title: "Error on attempt to update"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Award4thewin on 2010-10-06
Anyone know how to fix this? 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

tried manually running sudo dpkg but failed.  Also tried closing panels of gnome and going back to default settings:
[LEFT][COLOR=#ff0000]***gconftool – -recursive-unset  /apps/panel ***[/COLOR]
[COLOR=#ff0000]***[FONT=Verdana]rm -rf ~/.gconf/apps/panel[/FONT]***[/COLOR][/LEFT]
  [LEFT][COLOR=#ff0000]***[FONT=Verdana]pkill gnome-panel[/FONT]***[/COLOR][/LEFT]

 Still didn't work. When I tried pkilling it another error prompted telling me that something was in use.  

FRUSTRATED

---

### Post by jtarin on 2010-10-06
What package were you trying to install?
Try  ```
sudo dpkg --configure <packagename>
```
Refer to the command ```
man dpkg
```

---

### Post by Award4thewin on 2010-10-06
thank you for that, I appreciate the input.  It's just that I'm trying to install 46 updated packages... I think and I believe it's telling me that I have to do it manually which would be tedious and lame.  Any chance there's a way to streamline the operation?

---

### Post by jtarin on 2010-10-06
Why was Dpkg interrupted? It would help if you knew where the process was interrupted.
No it is telling you to run that command which will affect all.

---

### Post by Award4thewin on 2010-10-06
as soon as I tried the pkill line it gave me an error

---

### Post by jtarin on 2010-10-06
> **Award4thewin said:**
>   Any chance there's a way to streamline the operation?Yes run the command it tells you to in the terminal. You have to type it manually....sorry Ubuntu is'nt that advance to enter terminal commands.

---

### Post by jtarin on 2010-10-06
> **Award4thewin said:**
> as soon as I tried the pkill line it gave me an error
You've got two seperate issues going on. I suggest you post your panel problem under another topic.

---

