---
title: "Still Cannot Choose the Gnome Desktop at Log In"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by demarshall on 2009-02-27
Sometime ago somebody told me what to install in order to be able to log into Ubuntu with the Gnome desktop. Whatever it was I installed it but still cannot find a way to change my desktop manager when I log in. I'd really appreciate some help with this.

Thanks

---

### Post by fooman on 2009-02-27
a little more info please...

what are you booting into if not gnome?  ...kde?

try opening a terminal and type or copy/paste this command:

```
sudo dpkg-reconfigure gdm
```
is that doesn't work,  post back any errors you get.

---

### Post by demarshall on 2009-02-27
Yes, I normally use KDE. I don't want to permanently change my desktop. I just want the choice at Log in like I had previously. The command that you gave me sounds like it would permanently change my desktop.

---

### Post by fooman on 2009-02-27
at the login screen,  look in the bottom left and click on options > select session

then see if gnome is in the list,  if so...check it off and click on "change session"

or is it not on the list at all?

---

### Post by demarshall on 2009-02-27
I don't see anything on the log in screen aside from the small log in box in the center of the screen. There must be something that I need to have installed that isn't installed.

David

---

### Post by demarshall on 2009-03-05
Dumb! I just realized when I logged in yesterday that I could scroll the screen and that the session menu was at the bottom of the screen. I don't understand why whenever I restart my computer I have to reset my video mode so that my screen is the right size.

---

