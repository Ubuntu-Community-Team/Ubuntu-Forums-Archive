---
title: "restoring default trash icon?"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by WinterMadness on 2009-02-01
I changed it, and have no idea how to change it back to the default one. How do I do it?

---

### Post by squeabs on 2009-02-01
The new trash icon is probably part of a theme you selected to use, no?
If that's the case, just go to the "Appearance" menu and change the theme back to default.

---

### Post by WinterMadness on 2009-02-03
no it isnt part of the theme, i changed it.

im trying to make it so it changes back to the default (or the themes setting) and so that it changes when it has things in it. right now it just stays as one icon.

---

### Post by squeabs on 2009-02-03
Well, what if you remove the trash from the panel, then put a new one there?
Just a guess.
Here's a posting that might help: [http://ubuntuforums.org/showthread.php?t=318395](http://ubuntuforums.org/showthread.php?t=318395)

 I know it's from Edgy, but maybe the "empty" and "full" icons got a little mixed up. You may have to hunt those icons down and change them back to the original.

---

### Post by kansasnoob on 2009-02-03
Right click an open space on either panel then choose "add", then choose "Trash".

If that's what you want then right click the other icon and remove it.

---

### Post by Crafty Kisses on 2009-02-03
You could always just reinstall the icons, if you actually deleted the icon itself:
```
sudo apt-get install gnome-icon-theme
```

---

### Post by asmoore82 on 2009-02-03
I think the OP is trying to say that he customized the picture on the Desktop Trash Icon.

To restore this, open a terminal "Applications -> Accessories -> Terminal" and ...
```
cd .nautilus/metafiles/
mv x-nautilus-desktop\:%2F%2F%2F.xml  ~/
xkill
```

after you hit enter on "xkill," your mouse pointer will change to a kill icon to kill the next thing you click on -
click on the desktop **without** attempting to move or minimize any open windows.
This "xkill" step saves you the trouble of having to logout, if you get a bizarre message about nautilus can't restart, just click OK and it will try again.

That second command moves the file to your home folder, when you confirm that the fix works
with no bad side effects, you can go delete the file completely.
The easy way to type that second command is with the following exact keystrokes:
[m][v][space][x][tab][~][/][enter]

---

