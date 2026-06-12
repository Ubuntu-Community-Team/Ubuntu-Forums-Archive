---
title: "Accidentally clicked for Movieplayer to auto-launch on inserting DVD"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Garnett on 2010-06-15
How can I stop it doing this?

Thanks for any help.

---

### Post by stinkeye on 2010-06-15
System > preferences > file management > media

---

### Post by Garnett on 2010-06-16
> **stinkeye said:**
> System > preferences > file management > media
I don't have "File Management" as an option under "preferences".

I have "Preferred Applications, but the closest suboption under that is "Multimedia" and under that it says "Rhythmbox" is selected, which can't be the problem since it's "Movie Player" that automatically launches.

---

### Post by gandaran on 2010-06-16
nautilus»edit»preferences»media tab» dvd option» change to whatever you like it to do.

---

### Post by HomeSlixe on 2010-06-16
```
 **gksudo gedit /etc/gnome/defaults.list**
```
Press Ctrl+f and search for "x-content/video"
then change to whatever you like

---

### Post by mc4man on 2010-06-16
> Code:

 gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video"
then change to whatever you like 

Will ultimately prove to be a poor idea - post #4 is way to go 

( can also be opened with 
```
nautilus-file-management-properties
```

Or enable 'File Management' in edit menus -> preferences,
or even insert media and hold down shift button till pop up.

---

### Post by Garnett on 2010-06-16
> **gandaran said:**
> nautilus»edit»preferences»media tab» dvd option» change to whatever you like it to do.
> **mc4man said:**
> post #4 is way to go 

( can also be opened with 
```
nautilus-file-management-properties
```

Or enable 'File Management' in edit menus -> preferences,
or even insert media and hold down shift button till pop up.

Awesome! Many thanks guys - this is spot on.

---

