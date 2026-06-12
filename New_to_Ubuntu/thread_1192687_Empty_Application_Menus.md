---
title: "Empty Application Menus"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by TomGroff on 2009-06-20
Hi everbody

How can I remove an Item from the Applications Menu?

I Installed Wine and was testing installing Windows Apps.
The apps were added to the Applications menu under:
Wine | Programs | AppTitle | App.exe

Not knowing the proper way to remove an installed Wine app I located the app folder and simply deleted them.

Unfortunately the Wine Program sub menus are still there.

The Menu Edit Tool found under:  System | Preferences | Main Menu
Will not allow me to remove them.

How can I remove them from the menu?

---

### Post by shifty_powers on 2009-06-20
riight click on the top menu bar and select edit menus?

---

### Post by michy99 on 2009-06-20
Delete them from /home/YOURUSERNAME/.local/share/applications/wine/Programs.

---

### Post by Grrruff on 2009-06-20
Shifty:

What you suggest simply opens the same app that failed.
i.e. Menu Edit Tool found under: System | Preferences | Main Menu

Michey:

That worked I removed all subfolders under
/home/myUserName/.local/share/applications/Wine/Programs


but I also had to delete some files from the folder.
/home/myUserName/.local/share/applications. 
That bore the same names as the subfolders I removed.

Thank You and Cheers!

---

