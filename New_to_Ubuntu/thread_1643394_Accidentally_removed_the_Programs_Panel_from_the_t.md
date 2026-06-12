---
title: "Accidentally removed the Programs Panel from the top panel"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by Grunteh on 2010-12-11
I was trying to remove a seperator from the Top Panel and I accidentally removed the panel add-in that displayed programs, such as Skype and Steam. I looked through the add-in list, and I couldn't find it. Is there a way to re-add it?
(Ubuntu 10.10, just installed today)

---

### Post by diablo75 on 2010-12-11
Should be able to re-add it back to the panel by right-clicking on the panel and then clicking "Add to panel".  A little pop-up of menus and widgets will appear.  The one your looking for is called Main Menu I think.

---

### Post by Grunteh on 2010-12-11
No, I mean I removed the icons that show programs that are running in the background, such as skype.

---

### Post by karthick87 on 2010-12-11
Welcome to ubuntuforums :)
[SIZE=2]
In terminal type  these commands,[/SIZE]
```
gconftool-2 --shutdown
``````
rm -rf ~/.gconf/apps/panel
```[SIZE=3]
[/SIZE]```
pkill gnome-panel
```[SIZE=2]
All the panels should reappear without logging out.[/SIZE]
[SIZE=2]
[/SIZE]

---

### Post by Grunteh on 2010-12-11
> **karthick87 said:**
> Welcome to ubuntuforums :)
[SIZE=2]
In terminal type  these commands,[/SIZE]
```
gconftool-2 --shutdown
``````
rm -rf ~/.gconf/apps/panel
```[SIZE=3]
[/SIZE]```
pkill gnome-panel
```[SIZE=2]
All the panels should reappear without logging out.[/SIZE]
[SIZE=2]
[/SIZE]

That did it, thank you sir.

---

### Post by karthick87 on 2010-12-11
You are welcome :) If your problem is solved,pls mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

