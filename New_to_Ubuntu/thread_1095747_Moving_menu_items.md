---
title: "Moving menu items"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by mesmith on 2009-03-14
In Xubuntu, I want to an item from the applications menu "Accessories" to the menu "Multimedia".  Menu editor merely shows an "include system" line that does not appear to be editable.  Moving a menu item - it's a simple thing, but definitely NOT intuitive.

Any help with this trivial task?

---

### Post by balaknair on 2009-03-14
Open Menu editor--> Applications>Multimedia(or 'Sound and Video')> New Item(Copy the settings you find in 'Properties' from the app in the Accessories menu). Now uncheck the app in the Accessories menu.

Edit:
Oops. I'd assumed you were using Gnome, not XFCE. Sorry.

---

### Post by mesmith on 2009-03-14
This is Xubuntu.  No such opportunity.  Can't use your suggestion.

---

### Post by balaknair on 2009-03-14
For XFCE:
You need to edit the .desktop files in /usr/share/applications

Open the .desktop file for the app you want to change in Mousepad . Then edit the line starting with 'Categories=' to make it show up in Multimedia.

---

### Post by mesmith on 2009-03-14
Thanks.  That did it.  Dropped in "AudioVideo".  Exactly the results I wanted.

Mike

---

