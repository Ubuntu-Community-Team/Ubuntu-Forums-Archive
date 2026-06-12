---
title: "yes, another question from me"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by vnpifhf on 2010-01-16
right, how do you keep your background clean, because i have random things popping up and i have to unmount them all the time and would like to keep my desktop clear!!

Thanks

---

### Post by kenuf on 2010-01-16
Are you talking about filesystems and drives...
If so they usually appear when you access them.
For instance you put a CD in the drive...  Ubuntu mounts it and adds the icon to the desktop while it's mounted.

Is that what you are seeing?

---

### Post by vnpifhf on 2010-01-16
yes, when i access my hard drives/ pendrives they keep on popping up

and i have to keep on unmounting them

how do i stop this

---

### Post by sisco311 on 2010-01-16
Press Alt+F2 and run:
```
gconf-editor
```

go to apps/nautilus/desktop and deselect the *volumes_visible* checkbox.

---

### Post by TeoBigusGeekus on 2010-01-16
> **jahangir99 said:**
> yes, when i access my hard drives/ pendrives they keep on popping up

and i have to keep on unmounting them

how do i stop this
You have to keep on unmounting them, otherwise you're in danger of losing data when you take'em off your system.

---

### Post by vnpifhf on 2010-01-16
i think gconf-editor has worked but im not sure :/


well wait

---

### Post by Concrete on 2010-01-16
It will work.... you dont have to worry ;)

---

### Post by kenuf on 2010-01-16
Unmounting is the equivalent of 'Safely remove hardware' in Windows...
Windows just mounts and unmounts without asking.

I would encourage you to get used to it...  it could save you some heartache.

---

### Post by vnpifhf on 2010-01-16
aaah yes these things dont pop up anymore when i go to my computer to check files

solved

thanks :)

(many more Q to come) ;)

---

