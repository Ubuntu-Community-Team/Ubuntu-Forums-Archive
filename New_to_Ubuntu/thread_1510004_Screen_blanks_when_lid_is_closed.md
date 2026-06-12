---
title: "Screen blanks when lid is closed"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by robertelee on 2010-06-15
Is it possible to turn this feature off? I don't want it to do anything when I close the lid.
System: Dual booting Ubuntu 10.04 LTS and XP Home on an Asus EeePC, 1005HA, 1 GB DDR2,
1.6 GHz Intel Atom, etc, etc, standard netbook :confused:

---

### Post by Revolutionary101 on 2010-06-15
Go to System>Preferences>Power Management.

There you will find options for what you want the computer to do when the laptop lid is closed. You can also set it to do different actions when it is on AC (plugged in) or on battery power by clicking on the tabs above.

---

### Post by robertelee on 2010-06-15
> **Revolutionary101 said:**
> Go to System>Preferences>Power Management.

There you will find options for what you want the computer to do when the laptop lid is closed. You can also set it to do different actions when it is on AC (plugged in) or on battery power by clicking on the tabs above.
thanks, but it does not give an option to do nothing

---

### Post by 3rdalbum on 2010-06-15
It always at least blanks the screen to prevent heat from the screen from damaging the keyboard.

---

### Post by robertelee on 2010-06-15
> **3rdalbum said:**
> It always at least blanks the screen to prevent heat from the screen from damaging the keyboard.
requires password entry which is a pain, I can't turn that off either.....

---

### Post by an0dos on 2010-06-15
Go to System-->Preferences-->Screensaver and uncheck the block entitled something like "lock screen".

---

### Post by robertelee on 2010-06-15
> **an0dos said:**
> Go to System-->Preferences-->Screensaver and uncheck the block entitled something like "lock screen".
still no dice

---

### Post by kDDs on 2010-09-30
Incase you were still looking for a solution (had the same problem myself) this should work

Alt+F2 and type in "gconf-editor"

Then expand "apps" and find gnome-power-management click "buttons" and change the values of lid_ac and lid_battery to "nothing"

---

