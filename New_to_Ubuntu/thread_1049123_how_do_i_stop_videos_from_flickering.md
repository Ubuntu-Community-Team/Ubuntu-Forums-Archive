---
title: "how do i stop videos from flickering?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by insanity99 on 2009-01-24
i know turning desktop effects off works but i want to keep that on without constantly flickering videos. i am using Radeon HD 4870.

thanks

---

### Post by SunnyRabbiera on 2009-01-24
yeh its all on your card, some work better then others... especially ATI

---

### Post by insanity99 on 2009-01-24
so is there no way to fix this?

---

### Post by sdim on 2009-01-24
Only by using Compiz Switch.It's the safest way.

---

### Post by insanity99 on 2009-01-24
compiz switch?

---

### Post by CLomax on 2009-01-24
Look for the Compiz Fusion Icon in Add/Remove and select Metacity whenever you need to run a video.

That's the only way I can think of to get around it.

---

### Post by insanity99 on 2009-01-24
> **CLomax said:**
> Look for the Compiz Fusion Icon in Add/Remove and select Metacity whenever you need to run a video.

That's the only way I can think of to get around it.

this seems to work thanks! anyway i can get compiz fusion icon to start on log in?

---

### Post by 3rdalbum on 2009-01-24
You could donate some money to Xorg; they are working on the problem as we speak.

---

### Post by WatchingThePain on 2009-01-24
Yup turn off desktop effects. I don't know if using a different codec might work.

---

### Post by CLomax on 2009-01-24
> **insanity99 said:**
> this seems to work thanks! anyway i can get compiz fusion icon to start on log in?

System -> Preferences -> Sessions -> Add

Name: Fusion Icon (Or anything you want)
Command: fusion-icon

That should do it.

---

### Post by zika on 2009-01-24
> **insanity99 said:**
> i know turning desktop effects off works but i want to keep that on without constantly flickering videos. i am using Radeon HD 4870.

thanks
System->Preferences->Multimedia_Systems_Selector->Video->X_window_system(no xv)

---

### Post by philinux on 2009-01-24
In intrepid this menu item under prefs does not appear by default you have to tick it from the main menu editor..

---

### Post by zika on 2009-01-24
> **philinux said:**
> In intrepid this menu item under prefs does not appear by default you have to tick it from the main menu editor..
thank You for reminding me, I've forgot that ... ;)
nevertheless it works ... ;)

---

### Post by insanity99 on 2009-01-24
thanks guys. problem soved...kinda :D

---

