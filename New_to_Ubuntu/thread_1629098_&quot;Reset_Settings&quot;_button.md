---
title: "&quot;Reset Settings&quot; button"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Renegade Slim on 2010-11-23
The original post is below in quotes.  What I actually need to know is how to make my desktop not display the contents of my home folder as if it were the Desktop folder - it's embarrassing.




"In an attempt to "linux-ize" my Ubuntu's Gnome I deleted things like the Desktop Folder and My Documents (renamed to just documents).  I know I saw a reset settings button somewhere - where is it?

If there isn't one I just need to know how to make my home folder not show everything on the desktop like it was the desktop folder - it's embarrassing.

Thanks! :D"

---

### Post by eriktheblu on 2010-11-23
Have you tried ```
mkidir ~/Desktop
```

---

### Post by Renegade Slim on 2010-11-23
Ah... I think the problem is actually simpler than what I first wrote.  I just need what is in my home directory not to display on the desktop.  I installed Ubuntu on our other pc and it doesn't display home on the desktop by default.  I've botched it up somehow.   I would reinstall on this laptop but getting wpa to work with the wireless drivers isn't something I think I could do again.

Edited.

---

### Post by stinkeye on 2010-11-23
Alt + F2 and run 
```
gconftool-2 --set /apps/nautilus/preferences/desktop_is_home_dir --type bool FALSE
```


Then run
```
pkill nautilus
```

---

### Post by Renegade Slim on 2010-11-25
Oddly enough, only my Enlightenment desktop "cares" which folder is set as Desktop.  Gnome just rudely ignores the setting and continues on with home being desktop no matter the setting (and I played with gconf-editor after looking at and using the commands you gave me (thanks!))

---

