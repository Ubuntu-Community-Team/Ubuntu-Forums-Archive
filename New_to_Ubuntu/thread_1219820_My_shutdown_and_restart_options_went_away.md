---
title: "My shutdown and restart options went away"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by curiousnoob on 2009-07-22
I just installed Ubuntu 9 and the red power button on the top left corner of the screen no longer has a shutdown or reset option.  All that is left is Logout and Switch User.  
Does anyone know how I can get the shutdown feature back?

---

### Post by philinux on 2009-07-22
System>admin>login window>Local Tab

Tick the box "Show Actions Menu".

You must have been a fiddling lol.

---

### Post by Dullstar on 2009-07-22
Ubuntu 9?

I presume 9.04 Jaunty?

If so, click on where your username is displayed (top right hand corner) and then you will see your options.

Was this helpful?

---

### Post by curiousnoob on 2009-07-22
The "show actions" option is already ticked and my name does not appear at all in the upper corner of the screen, or anywhere else for that matter.  
Any ideas what might be happening here?

---

### Post by LookTJ on 2009-07-22
Seems like you removed it from the panel.

Try right clicking on the top panel and find the option "Add to panel"

Look through the options listed and hopefully you can find it.

---

### Post by NOTAGEEK on 2009-07-22
Right-click on your panel, click Add To Panel, Notification Area.

---

### Post by curiousnoob on 2009-07-22
OK, I'm definitely doing something really wrong.  
When I right click on the bar at the top of the screen the options I get are Help and About Panels.

---

### Post by ukripper on 2009-07-22
Did you install ubuntu-desktop through kubuntu? if that is the case then you need to change your default kdm to gdm

---

### Post by curiousnoob on 2009-07-22
> **ukripper said:**
> Did you install ubuntu-desktop through kubuntu? if that is the case then you need to change your default kdm to gdm

No, all I did was hit the Update button and follow the instructions.  This is weird.

---

### Post by fooman on 2009-07-22
right-click on a *blank* area of the top panel and choose "add to panel"

go through the list and find "shut down"....add it to panel,  then right click on it and choose "move" to put it where you want.  hope that helps.

---

### Post by curiousnoob on 2009-07-22
> **fooman said:**
> right-click on a *blank* area of the top panel and choose "add to panel"

go through the list and find "shut down"....add it to panel,  then right click on it and choose "move" to put it where you want.  hope that helps.

Same thing.  I have right clicked on every part of the bar and get the same result.

---

### Post by s.fox on 2009-07-22
How strange :confused:.  

Did you used to have it?  If so what  were you doing prior to it disappearing?   

-Silver Fox

---

### Post by fooman on 2009-07-22
i think you can fix this with the gconf editor.  open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
gconf-editor
```

when it opens,  go to apps > panel > global

look for "lock down" on the right side and uncheck it.

then right click the panel and see if the other options are there.

hope that helps.

---

### Post by meeples on 2009-07-22
sounds like youve installed karmic...9.10

in karmic the shutdown restart buttons have moved to the "system" menu. have look there.

you can check System > Admin > System Monitor to see if it says your running 9.04 or 9.10.

definately sounds like 9.10 though. hmm.

---

### Post by curiousnoob on 2009-07-22
> **fooman said:**
> i think you can fix this with the gconf editor.  open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
gconf-editor
```

when it opens,  go to apps > panel > global

look for "lock down" on the right side and uncheck it.

then right click the panel and see if the other options are there.

hope that helps.

You are the man.  That fixed it.  Thank you my good sir.

---

