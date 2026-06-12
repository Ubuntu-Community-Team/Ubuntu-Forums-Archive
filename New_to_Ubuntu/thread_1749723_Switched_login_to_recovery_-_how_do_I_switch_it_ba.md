---
title: "Switched login to recovery - how do I switch it back?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by kdnoel on 2011-05-04
Went into the system settings and changed login to recovery... it boots and login brings up terminal.

How do I get out of it and go back to booting Ubuntu?

Thanks!

---

### Post by Tim Sharitt on 2011-05-04
Do you login automatically or do you have to enter a password? If it's the latter, just change the session type from the combo box at the bottom of the screen.

---

### Post by fremantle on 2011-05-04
try 
> startx

in terminal. it will start the x window.

---

### Post by fremantle on 2011-05-04
alright, if startx dont work, this will restart gnome
> sudo /etc/init.d/gdm restart

---

### Post by Tim Sharitt on 2011-05-04
If you do login automatically, run gdmsetup and reset the default session.

---

### Post by Tim Sharitt on 2011-05-04
> **fremantle said:**
> alright, if startx dont work, this will restart gnome

This restarts gdm which will ,without automatic login, bring up the login screen or, with automatic login, restart the same type session (in this case, failsafe terminal).

---

### Post by kdnoel on 2011-05-04
> **Tim Sharitt said:**
> Do you login automatically or do you have to enter a password? If it's the latter, just change the session type from the combo box at the bottom of the screen.

Thank You!

I am a little frustrated... my original problem is that since upgrading I have no grub menu option to boot to Xp from.
I can still see my Xp drive and mount it.
I have reinstalled grub but I just get an out of range error and then finally boot to Ubuntu.

---

