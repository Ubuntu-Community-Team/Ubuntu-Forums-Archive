---
title: "Administrative rights"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by icyest on 2009-02-16
Is there a way to give yourself temporary administrative rights? I'm sick of having to go down a winding path of terminal > "sudo nautilus" in order to do things with my computer files. It just takes too long. I wish there some sort of button (or anything really) that can give me instant admin rights because all I need to do is one thing.

(if you're wondering, I'm trying to stick in a theme for the "Clock" screenlet, but it's in /usr/share/screenlets/Clock/themes and I cant seem to drag and drop a new theme because nautilus won't let me. The only way I could do it was Terminal -> type in sudo Nautilus and then do it. I constantly find myself having to do this. There has to be an efficient way. This is linux after all.)

---

### Post by Cl0ud9 on 2009-02-16
You can add an item in your menus to accomplish this.

1. Right click on the top panel where it says "Application" and select "Edit Menus".
2. Choose the submenu on the left side of the screen where you want to place the new item. For an example, I chose "Administration" under "System".
3. Click new item on the right side of the screen.
4. Change type to "application".
5. Give it a name.
6. Enter "gksudo nautilus" as the command without the quotes.
7. Click "OK" and you should be good to go.

---

### Post by Michael Dooley on 2009-02-26
Thanks Cl0ud9, I've been looking for this information for weeks.

---

### Post by capnthommo on 2009-02-26
hi Cl0ud9.  +1 from me too.  i assume i can use the same procedure for other similar kinds of operations?
thanks again
nigel

---

### Post by snova on 2009-02-26
> **capnthommo said:**
> hi Cl0ud9.  +1 from me too.  i assume i can use the same procedure for other similar kinds of operations?
thanks again
nigel

Creating menu items for other programs with administrative priviliges? Yes, as long as you know the name of the command.

(Which can be found by opening the menu editor, and clicking the Properties button on the item in question.)

---

