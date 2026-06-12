---
title: "How to remove mount icon from my desktop"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by nakama85 on 2009-10-31
I have set a new hdd to automount. I noticed it has an icon on the desktop. I would like to remove this icon and just place a shortcut to the new hdd in my home folder.

any ideas?

---

### Post by fooman on 2009-10-31
go to applications > system tools > configuration editor

in the editor,  on the left side...go to apps > nautilus > desktop

look on the right side and uncheck "volumes_visible"

that should get rid of the desktop icon.  there should already be a shortcut for it under "places".

hope that helps. :)

---

### Post by nakama85 on 2009-10-31
> **fooman said:**
> go to applications > system tools > configuration editor

in the editor,  on the left side...go to apps > nautilus > desktop

look on the right side and uncheck "volumes_visible"

that should get rid of the desktop icon.  there should already be a shortcut for it under "places".

hope that helps. :)

Thanks but I dont see system tools under the Applications menu. Should I?

---

### Post by NoaHall on 2009-10-31
It's not there by default. Instead, open the terminal (under accessories) and run "gconf-editor"

---

### Post by fooman on 2009-10-31
> **NoaHall said:**
> It's not there by default. Instead, open the terminal (under accessories) and run "gconf-editor"

yeah,  that'll work.  :p

you could also add system tools to the menu if you like.  *right*-click on applications and choose "edit menus"

when the main menu pops up,  look on the left and click once on "applications"....then look on the right and put a check next to "system tools".

---

### Post by nakama85 on 2009-10-31
> **fooman said:**
> go to applications > system tools > configuration editor

in the editor,  on the left side...go to apps > nautilus > desktop

look on the right side and uncheck "volumes_visible"

that should get rid of the desktop icon.  there should already be a shortcut for it under "places".

hope that helps. :)

> **NoaHall said:**
> It's not there by default. Instead, open the terminal (under accessories) and run "gconf-editor"

Thanks, This Worked Perfectly!!

---

### Post by dj-toonz on 2009-10-31
Or if you don't want to keep doing that all the time, right mouse on Applications, Edit menus , System Tools & tick Configuration Editor then close

---

