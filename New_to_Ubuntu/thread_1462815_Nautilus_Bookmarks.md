---
title: "Nautilus Bookmarks"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by holomorpholutionary on 2010-04-26
I'm running 10.04 and I wanted to reset the Nautilus Bookmarks back to their defaults... I accidentally added a *lot* of folders to the bookmarks and the file browser hangs every time I try to get rid of these bookmarks from there. I tried deleting and replacing ~/.gtk-bookmarks, but all of the unwanted bookmarks just come right back.. How can I reset the bookmarks back to the defaults?

Thanks.

---

### Post by user1397 on 2010-04-26
Might be able to do it with the gconf-editor, but I'm not sure I gotta look that up more...

---

### Post by Irony on 2010-04-26
Perhaps use a live cd to mount you drive and delete ~/.gtk-bookmarks from there or set up another user and delete ~/.gtk-bookmarks from there - in other words delete ~/.gtk-bookmarks when nautilus isn't mounted (as it would be when you boot into your user).

---

### Post by matti.p on 2010-07-02
I was looking for an answer to this and foudn it somewhere else, but wanted to post in case someone else gets here.

Open a file browser window (Places->Home Folder will do fine), then check out the Bookmarks menu.

Matti

---

### Post by e.m.fields on 2010-08-04
Yeah, this was "buggin" me too. (yuk yuk. sorry.)

So, I looked it up.  
Apparently, known bug:
[https://bugs.launchpad.net/nautilus/+bug/549707]("https://bugs.launchpad.net/nautilus/+bug/549707")

No solution as of yet.
FYI, your bookmarks are stored under home folder as .gkt-bookmarks
(If you open nautilus, navigate to home folder, hit "control H" to view hidden files, you'll see it.)

If you find a solution, hope you'll report it here.

---

### Post by e.m.fields on 2010-08-04
Whoah! Solution found: (Well, sort of.)

BUG:
Bookmarks are not updated when renamed in Nautilus file browser

SOLUTION (Workaround):
[B]Update bookmark names from Bookmarks menu (At top menu list, Bookmarks > Edit Bookmarks, NOT from bookmarks side panel!)
Bookmark names will be immediately changed in side panel.
[/B]
from Nautilus bug report:
[http://osdir.com/ml/debian-bugs-dist/2010-03/msg03185.html]("http://osdir.com/ml/debian-bugs-dist/2010-03/msg03185.html")
> Try to rename a bookmark from the side panel of nautilus:
1. the name is not updated immediately in the side panel (it is in nautilus'
Bookmarks menu). Nautilus has to be closed and reopened for the
change to appear.
2. the name is not update in the Places/Bookmarks menu (of Gnome panel)
3. quitting (with --quit) and restarting nautilus, the old name is back

However, bookmarks rename works fine from the Eookmarks/Edit bookmarks menu of
nautilus.


---

