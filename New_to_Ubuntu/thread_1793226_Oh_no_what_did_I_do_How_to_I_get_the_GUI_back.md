---
title: "Oh no what did I do??? How to I get the GUI back?"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by Rockworthy on 2011-06-29
Hello Ubuntu forums!  I'm such a noob: I was on the log in screen.  I wanted to see if Ubuntu could give me a list of other "sessions" to try, (such as KDE or GNOME) or whatever.  I'm very new to Linux and Ubuntu.  I thought I could try GNOME just by clicking on "user defined" on the little area at the bottom of the login screen where you have a choice of something like, "Ubuntu classic," etc.  But now here's the problem... after choosing "user defined" when I start Ubuntu now all I get is my wallpaper and nothing else is visible!!! How do I get my GUI back?  I can launch a Terminal window by pressing ctrl+Alt, T, but I have no idea how to get my regular Ubuntu GUI back.  Can anyone help me?  Thanks!

---

### Post by LowSky on 2011-06-29
```
gnome-session-save --force-logout
```

that should get you to the log in screen to make changes

---

### Post by ajgreeny on 2011-06-29
I presume also that **Alt Gr+Print Screen+K** will kill your session and take you to the login screen again, where you can choose what you want.

---

### Post by createdcreature on 2011-06-29
Type in the terminal (without the speech marks) 'sudo su', type your password, and then type 'init 5'.

---

### Post by Monotoko on 2011-06-29
> **Robert Moyse said:**
> Type in the terminal (without the speech marks) 'sudo su', type your password, and then type 'init 5'.

That won't work, he's already on runlevel 5, all he has changed is the desktop session being used.

---

### Post by Rockworthy on 2011-06-29
> **LowSky said:**
> ```
gnome-session-save --force-logout
```that should get you to the log in screen to make changes

OMG you did it!!! That was it you fixed it!  Thank you so much, you are a genius.  *Also, I love your Einstein quote.

---

