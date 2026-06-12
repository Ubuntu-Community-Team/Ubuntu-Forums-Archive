---
title: "go to theme folder button"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by knuckle dragging monkey on 2009-06-07
Hello, I am trying to install a new cursor into the cursor selection. I have downloaded a cursor theme onto the desktop unpacked and clicked install theme and it did not appear. then i unpacked it and clicked install theme and still did not appear. then i clicked on go to theme folder and no folder appeared. so what am i doing wrong any suggestions. Thank you.

---

### Post by NilsE on 2009-06-07
Cursors  are installed in the icon folder. Either /usr/share/icons or the one in your home folder.

If it is not showing up as selectable in the appearance applet under customize check those 2 folders and see if it is really there.  If not go into a terminal and run "gksudo nautilus" (without the quotes)and browse to the archive you downloaded.  Then open the archive and browse to /usr/share/icons and extract it with the create folders option checked.

---

### Post by knuckle dragging monkey on 2009-06-07
Thank you very much I will do that.

---

