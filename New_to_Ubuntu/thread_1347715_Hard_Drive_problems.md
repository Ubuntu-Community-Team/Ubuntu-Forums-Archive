---
title: "Hard Drive problems"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by disse on 2009-12-06
hi all,

i've just started using ubuntu, v9.10. When i try to acces my external HDD (WD500gb)via the icon on my desktop, the icon disappears, and all open windows close. I can still access the files on the HDD in the terminal, but can't seem to get it working in the GUI. Any ideas?

---

### Post by aktiwers on 2009-12-06
What happens if you open through terminal(Application=> accessories=>terminal)?
```
nautilus /media/*HARDRIVE*/
```where* HARDRIV*E is the mountpoint (name) of  your WD500 hardrive.

---

### Post by disse on 2009-12-07
> **aktiwers said:**
> What happens if you open through terminal(Application=> accessories=>terminal)?
```
nautilus /media/*HARDRIVE*/
```where* HARDRIV*E is the mountpoint (name) of  your WD500 hardrive.

i get:

(nautilus:3292): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension
Segmentation fault
thomas@thomas-laptop:~$ ^C

---

### Post by ScottinSoCal on 2009-12-07
I would guess you've got a corrupted external hard drive. When you access it through the GUI it does several things that don't happen in a terminal. I'd bet if you tried to (for example) get a complete directory listing of all folders, it would puke the ls command.

---

### Post by disse on 2009-12-07
> **ScottinSoCal said:**
> I would guess you've got a corrupted external hard drive. When you access it through the GUI it does several things that don't happen in a terminal. I'd bet if you tried to (for example) get a complete directory listing of all folders, it would puke the ls command.

i haven't got any problems working in the terminal, i can ls and copy from and to the harddisk. Also, in windows it doesn't give any problems. Can i do anything to fix this?

---

### Post by dragon0788 on 2009-12-07
This happened to me

---

### Post by ScottinSoCal on 2009-12-07
> **disse said:**
> i haven't got any problems working in the terminal, i can ls and copy from and to the harddisk. Also, in windows it doesn't give any problems. Can i do anything to fix this?

The easiest thing to do would be to reformat the drive, but you'll lose everything on it. If you can copy the files off (but, again, that may make your system puke, even in a terminal window) you should be able to move them back onto the external hard drive.

The other possibility is a failing USB/IDE interface in your external case, but that would typically show up whether you were in a GUI or not - you'd get read/write errors.

The corrupted hard drive is the most common, and most easily and inexpensively fixed problem, so I'd go that route first. If that doesn't do it, a new external hard drive case would only be ~USD$20 or so. That would be my second route.

---

