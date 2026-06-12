---
title: "Places Bookmark path error"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by SJ2011 on 2011-04-02
Hello Ladies and Gents, I am having a problem with my Gnome-Panel "Places" Bookmark. When I click on any of the links (Video, Download, Musics, etc...) it always takes me to the "Appearance Preferences. I tried "Edit Bookmarks" and the path seems to be okay. Help will be much appreciated. Thank you.

---

### Post by PCNetSpec on 2011-04-02
Open a terminal and enter:

```
gedit ~/.local/share/applications/mimeapps.list
```

now look for an entry that starts with:

**inode/directory=**

if you find one, comment it out, ie. so it starts with **#**

eg.
# inode/directory=gnome-appearance-properties.desktop;

Save the file, and try your bookmarks now.

---

### Post by SJ2011 on 2011-04-03
PCNetSpec, you the man...thanks a lot! It worked perfectly.

---

