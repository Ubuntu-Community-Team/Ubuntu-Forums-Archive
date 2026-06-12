---
title: "I messed up Big Time"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by shadowman444 on 2009-01-26
Ok so, I have a school computer that is supposed to be completely private. However, although we are assigned computers people keep coming onto my computer. So in retaliation, I deleted their things. The next day my computer was loaded with more documents, work etc. So finally I got sick of it and I changed the username and password however I completely forgot the username. I know the password but is there any other way to get onto the computer to change the username and log back in?

I have Ubuntu Gnome version 2.22.2

---

### Post by taurus on 2009-01-26
Boot into recovery mode from GRUB menu and get into root shell.  Then, look in /home to see what your new username is.

```
ls -la /home
```
You can reset your password from that prompt to.

```
passwd *username*
```
Type **exit** if you are all done.

---

### Post by shadowman444 on 2009-01-26
Hey thanks so much, really, I appreciate it so much.

---

