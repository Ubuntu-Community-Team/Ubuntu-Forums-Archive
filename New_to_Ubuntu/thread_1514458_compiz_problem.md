---
title: "compiz problem"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by kiraku on 2010-06-21
hi:

i activate the visual efect "reflejo" (in spanich)... it may be "reflex"  (literal translation)...
and now my pc it stay "frozen"... i cant do anything...

there is a way to desactivate this efecto trough the recovery mode... (on the terminal)...??

cya

---

### Post by Blodskaal on 2010-06-21
I have no idea how to fix this, but I think the correct translation for "reflejo" is "reflection". I don't know that much about spanish, but my english ccmp has no 'reflex' visual effect afaik. However it does have 'reflection' effect.

---

### Post by warfacegod on 2010-06-21
Select the "Recovery" kernal in GRUB. When it loads, drop to a shell and type: startx

That will put you into the root account (be careful). Use it to disable Reflection. You may need to mark ccsm for complete removal in Synaptic and then install it again.

---

### Post by kiraku on 2010-06-21
hi:

i enter as root, but there the reflection efect is disabled... and for my user is not...???

so, how i disable it just for my user?

---

### Post by warfacegod on 2010-06-21
Try this. Get to the login screen and put your username and passwork in but before you click Login, change the session to "Safe".

---

### Post by lkjoel on 2010-06-21
Ok, go into root, then type in a terminal (Applications->Accessories->Terminal):
```
rm /home/(your_user_name_who_has_compiz_problems)/.compiz
```
That should fix it.

---

### Post by kiraku on 2010-06-21
yeah, but i have setted that at start, automatically login to my account, and now i cannot disable this as root (gdmsetup)... it not let me...

????????

---

### Post by kiraku on 2010-06-21
> **lkjoel said:**
> Ok, go into root, then type in a terminal (Applications->Accessories->Terminal):
```
rm /home/(your_user_name_who_has_compiz_problems)/.compiz
```That should fix it.

that will remove compiz???
and then i have to install it again??

thanxz

---

### Post by warfacegod on 2010-06-21
No, that should simply delete the settings file for Compiz reverting it back to it's defaults.

---

### Post by lkjoel on 2010-06-21
No it will not remove compiz.
It will remove the compiz configuration files for that user.
It will not affect the compiz *application* in any way.

---

### Post by kiraku on 2010-06-21
> **lkjoel said:**
> Ok, go into root, then type in a terminal (Applications->Accessories->Terminal):
```
rm /home/(your_user_name_who_has_compiz_problems)/.compiz
```That should fix it.

hi again...

that doesn't work... when i start my user, it happens again...

---

### Post by lkjoel on 2010-06-21
Sorry, try this in root instead
```
rm /home/(your_user_name_who_has_compiz_problems)/.config/compiz
```
Now it should work.

---

### Post by kiraku on 2010-06-21
hi:

this works for me:

rm -r ~/.gconf/apps/compiz

thankz anyway

---

### Post by lkjoel on 2010-06-21
No problem, I'm glad you were able to fix it!

---

