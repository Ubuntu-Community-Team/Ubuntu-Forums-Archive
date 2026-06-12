---
title: "Very Little Problem"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Papenco on 2008-12-30
Okey, I Don't Know How, a folder moved to my Places Menu.
When I Click on It, I get 
Personal Folder
Desktop
Documents
Music
Videos
Galactic Supermarket (THIS IS THE FOLDER)

Okey, how can I take it outta there?

---

### Post by eBoxNet on 2008-12-30
try to right click on places and then click edit menu..

---

### Post by taurus on 2008-12-30
You want to delete ~/Desktop/"Galactic Supermarket" directory?

Applications -> Accessories -> Terminal
```
cd ~/Desktop
rm -rf "Galactic Supermarket"
ls -la
```

---

### Post by eBoxNet on 2008-12-30
i think he just don't need the dir link in "places" menu...

---

### Post by drs305 on 2008-12-30
Be careful here. You might want to more fully explain what you want to do.

If you only want to remove the **shortcut** on the Places menu in Nautilus - a folder name in the bottom part of the Places menu, just right click the name and select "Remove". This entry is only a shortcut to the actual folder, which you probably don't want to delete. This action would take place in the *left* panel in Nautilus.

---

### Post by Papenco on 2008-12-30
Thanks for your help:
What I want to do is to remove the shortcut, when I right click it, it just opens. And I can't get to edit the Places Menu.

---

### Post by adult swim on 2008-12-30
go to places>home folder
when that opens up look up at the top and go to bookmarks.  then choose edit bookmarks.  find the bookmark you want to remove on the left and highlight it.  then choose remove bookmark.

---

### Post by Papenco on 2008-12-30
Thanks, that was what I was searching for.

---

