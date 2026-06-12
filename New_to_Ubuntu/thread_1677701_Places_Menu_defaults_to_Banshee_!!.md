---
title: "Places Menu defaults to Banshee ?!?!"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-01-29
When I click on the places menu, i can see all my bookmarks...but when I click on them Banshee opens....even when I kill Banshee, clicking on the bookmark opens Banshee. I have gone into Nautilus and checked the link to the bookmarks and they are all OK.....any idea what might be happening here?

---

### Post by davidmohammed on 2011-01-29
your issue reads remarkably similar to [this thread]("http://ubuntuforums.org/showthread.php?t=1505483").  Hope it helps.

---

### Post by coffeecat on 2011-01-29
The easy way of fixing this is to right-click on the desktop and create a folder. Right-click on the folder and 'Open with other application'. Make sure the 'Remember this application..." box is ticked and scroll down the list and open it with 'File Browser'. You can now delete the temporary folder on the desktop.

This is a common issue with all sorts of media players. It probably happens when a folder is opened with a right-click to the media player and the 'remember' box is left ticked.

---

### Post by supererki on 2011-01-29
the paths to your places booksmarks should be hardcoded in :

.gtk-bookmarks 

Check the file and edit it

cat .gtk-bookmarks

---

### Post by yetiman64 on 2011-01-29
OP, bookmarks are only links to open a folder (normally associated to Nautilus aka File Browser). 

No need to edit them. Just run the fix coffeecat posted. It should work as even I've posted the same instructions here at times with success.

---

### Post by dunbrokin on 2011-01-29
> **coffeecat said:**
> The easy way of fixing this is to right-click on the desktop and create a folder. Right-click on the folder and 'Open with other application'. Make sure the 'Remember this application..." box is ticked and scroll down the list and open it with 'File Browser'. You can now delete the temporary folder on the desktop.

This is a common issue with all sorts of media players. It probably happens when a folder is opened with a right-click to the media player and the 'remember' box is left ticked.

Great tip, thanks...that worked a treat.

---

