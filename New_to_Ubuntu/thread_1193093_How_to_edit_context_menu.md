---
title: "How to edit context menu?"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by adit on 2009-06-21
I want to change the entries in context menu.  In which file these entries are saved.  Is it a text file or a database file (binary)?  If it is a text file, I can edit them directly.

---

### Post by rraj.be on 2009-06-21
Actually what do you mean by context menu?

---

### Post by adit on 2009-06-21
> Actually what do you mean by context menu?The menu that appears when I right click some icon in the Desktop.

---

### Post by adit on 2009-06-23
Anyone?

---

### Post by aeiah on 2009-06-23
have a look at nautilus-actions. if you use nautilus, that is.

---

### Post by mc4man on 2009-06-23
If  you right click -> properties -> 'open with' with you can add, remove, and create ( to create click add -> use custom command

Entries that you've added from various means are stored in 
~/.local/share/applications
and are showing up due to being on an appropriate line in 
~/.local/share/applications/mimeapps.list

(some r. click options are available when an app installs and registers as a mimetype, in that case you usually won't see them there.

Thread with slightly more info on  ~/.local/share/applications, ect.
[http://ubuntuforums.org/showthread.php?t=1192351](http://ubuntuforums.org/showthread.php?t=1192351)

(noting that ~/ means home folder, and .local is a hidden file (Ctrl+h or view -> show hidden files if not visible

---

