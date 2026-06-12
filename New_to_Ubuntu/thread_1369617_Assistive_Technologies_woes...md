---
title: "Assistive Technologies woes.."
date: 2010-01-01
forum: New to Ubuntu
---

### Post by JPA2 on 2010-01-01
This morning on the log in screen, I clicked on the assistance technologies icon to paruse the features being new to ubuntu , about 6 months, i clicked on the magnify option and this is where my troubles begin.  I have two  dell 22" monitors, on the left monitor i see the login screen just fine, on the right monitor it is magnified and the login screen is jazzed, moving the entire page when moving the mouse, My question is this, how do return my login screen back to a normal state, without the magnify on? I forgot to mention that I cannot click the assistive technologies icon now.  Any help would be appreciated.

---

### Post by Indigothecat on 2010-08-19
Hi 

Just a "Bump" as I have the same problem at the login screen but only one monitor. Anyon know the hotkeys for assistive technologies functions. 

Many thanks

---

### Post by bearslumber on 2011-10-26
Why is this thread marked as [Solved]? There does not seem to be any solution documented.

:confused:

---

### Post by bearslumber on 2011-10-26
Okay,

After searching the forum the solution is as follows:

Boot into recovery mode.
Choose the root prompt.
From the root prompt type in the following command

```
sudo dpkg remove gnome-mag
```

This removes the magnifier from your install altogether. You need to do the reverse to get it back.

If your child has set the "slow keys" you will need to reset that from the assistive  icon at login.

Hope that helps.

Mr Bear

---

