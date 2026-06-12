---
title: "location of gnome log out session button on panel"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by zff4 on 2009-05-03
After I've logged in, the log out button in the top right corner of the panel is a green running man.  

I changed it once to an icon I prefer but now that I've upgraded to jaunty, it's reverted.

Where is the gnome green running man logout icon located?
cheers

---

### Post by zff4 on 2009-05-03
After I've logged in, the log out button in the top right corner of the panel is a green running man ("Log out of this session...").

I previously changed it to an icon I prefer but now that I've upgraded to jaunty, it's reverted.

Where in the file system is the gnome green running man logout icon located and what is the file's name? I wish to replace it with an icon of my preference.
cheers

---

### Post by _Purple_ on 2009-05-03
You can find the icon here

/usr/share/icons/gnome/24x24/actions/system-log-out.png

---

### Post by RedSingularity on 2009-05-03
Change your icon theme in System>preferences>appearance.

---

### Post by zff4 on 2009-05-03
> **_Purple_ said:**
> You can find the icon here

/usr/share/icons/gnome/24x24/actions/system-log-out.pngActually it's not.  I've changed all instances of the green running man found there and the "log out of this session" icon located at the top right of the panel remains the green running man.  Where, I wonder, is this particular icon located, and can I change it?

---

### Post by _Purple_ on 2009-05-03
> **zff4 said:**
> Actually it's not.  I've changed all instances of the green running man found there and the "log out of this session" icon located at the top right of the panel remains the green running man.  Where, I wonder, is this particular icon located, and can I change it?

In /usr/share/icons/gnome/ directory, you have 16x16, 22x22, 24x24, 32x32 48x48 8x8 and scalable. So the icon is in more than one directory. I do not know which one is it using.

---

### Post by pastalavista on 2009-05-03
If you right-click the panel and check the properties, you can change the size of the panel... one of the icons you changed might show up when the panel is the corresponding size.. so change the one that matches the size of the panel. You might also look in /user/share/pixmaps

edit: never mind pixmaps.. just speculation... wrong

---

### Post by zff4 on 2009-05-03
> **_Purple_ said:**
> In /usr/share/icons/gnome/ directory, you have 16x16, 22x22, 24x24, 32x32 48x48 8x8 and scalable. So the icon is in more than one directory. I do not know which one is it using.The system action of the log out button has changed for the jaunty release.  The location of the icon has also changed.  But to where?

---

### Post by zff4 on 2009-05-03
> **pastalavista said:**
> If you right-click the panel and check the properties, you can change the size of the panel... one of the icons you changed might show up when the panel is the corresponding size.. so change the one that matches the size of the panel. You might also look in /user/share/pixmapsgood suggestion but it didn't work.  The icon scales but I've changed all the icons in the scalable folder.  It remains a mystery.

I surely am not the only person who has tried to change this icon.  That green running figure is horrid and I want to be quit of him.

---

### Post by zff4 on 2009-05-04
> **_Purple_ said:**
> You can find the icon here

/usr/share/icons/gnome/24x24/actions/system-log-out.png

Unfortunately not.  I earlier changed that icon to no effect.  That may have been the location in Gutsy, but but not in Jaunty.

---

