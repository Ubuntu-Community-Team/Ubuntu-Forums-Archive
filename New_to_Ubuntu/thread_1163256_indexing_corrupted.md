---
title: "indexing corrupted?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by eheitner on 2009-05-18
I'm getting an dialog box "Tracker Applet"
"There was an error while performing indexing:
index corrupted"
reindex all contents  / cancel / ok

When I say reindex, I get

"Are You Sure? Reindexing can take a long time."
I hit yes or no, doesn't matter, just takes me back to the previous dialog box. 

Also makes no difference if I hit cancel or ok at that dialog box, just pops up again.

---

### Post by eheitner on 2009-05-18
Oh, and this seems to occur when I plug my ipod in.

---

### Post by mprince on 2009-05-18
Under *System>Preferences>Search and Indexing* you can choose to ignore files (and I assume folders). You can also adjust how the tracker behaves in general.

Hopefully, you can set it to 'ignore' your ipod or try unchecking 'index mounted directories'.

---

### Post by mprince on 2009-05-20
This is actually a known bug. This is taken from the 9.04 release notes:

> Tracker index corruption

In some cases it can happen that the index of the "tracker" desktop search engine becomes invalid. A dialog will be shown, offering you to "Reindex all contents". This button does not work, and the tracker service might start to use large amounts of CPU and disk resources. [COLOR="Blue"]As a workaround, please press Alt+F2 and run **tracker-processes -r**[/COLOR]. This will be fixed in a post-release update soon

---

