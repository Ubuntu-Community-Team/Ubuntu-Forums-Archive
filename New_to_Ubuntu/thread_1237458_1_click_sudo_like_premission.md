---
title: "1 click sudo like premission?"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by andru183 on 2009-08-11
im using gnome and somtimes i try to move or delete files that ive made (i know there not tied directly to a progam) but in the /etc so some times i dont have permission to move/delete/edit them, is there a way that i could set up a command launcher from the menu system for something like sudo nautilus, ive tried putting that into the menu command slot but it never open anything or asks for a password so i figure its not working, or is this just silly to ask?

---

### Post by aysiu on 2009-08-11
Yes, there is:
[Make a &#8220;browse as root&#8221; launcher in Ubuntu](http://www.psychocats.net/ubuntucat/rootlauncher/)

And it should be *gksudo nautilus*, not *sudo nautilus*.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mapes12 on 2009-08-11
> And it should be gksudo nautilus, not sudo nautilus.Nope. Correct command is ```
gksu nautilus
``` although the other one will work.

**VERY IMPORTANT:** When deleting anything using nautilus with this command press the "Shift" key then the delete button on your keyboard. Why? Because otherwise you will end up filling up Roots waste basket with stuff that's not permanently deleted off your system and you will wonder why your HDD is full. See here: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by MrWES on 2009-08-11
> **andru183 said:**
> im using gnome and somtimes i try to move or delete files that ive made (i know there not tied directly to a progam) but in the /etc so some times i dont have permission to move/delete/edit them, is there a way that i could set up a command launcher from the menu system for something like sudo nautilus, ive tried putting that into the menu command slot but it never open anything or asks for a password so i figure its not working, or is this just silly to ask?

You can also place this script in 
```
~/.gnome2/nautilus-scripts/
```

Drop the .txt extension and make it executable, restart Nautilus if running, and now the script is available when you click the right mouse button.

Bill

---

### Post by wojox on 2009-08-11
> **mapes12 said:**
> Nope. Correct command is ```
gksu nautilus
``` although the other one will work.
**VERY IMPORTANT:** When deleting anything using nautilus with this command press the "Shift" key then the delete button on your keyboard. Why? Because otherwise you will end up filling up Roots waste basket with stuff that's not permanently deleted off your system and you will wonder why your HDD is full. See here: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Nope correct command is:
```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by aysiu on 2009-08-11
```
gksudo nautilus
``` and ```
gksu nautilus
``` are actually the same thing.

---

### Post by Viva on 2009-08-11
You can also use [nautilis gksudo extension]("apt:nautilus-gksu")

---

### Post by mapes12 on 2009-08-11
> **aysiu said:**
> ```
gksudo nautilus
``` and ```
gksu nautilus
``` are actually the same thing.

Just remember the "Shift" key to permanently delete.

---

### Post by andru183 on 2009-08-11
wow thanks guys thats as helpful as it gets!

---

