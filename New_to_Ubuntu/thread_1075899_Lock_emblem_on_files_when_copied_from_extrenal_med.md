---
title: "Lock emblem on files when copied from extrenal media or Trash"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by MockY on 2009-02-20
When ever I drag-n-drop items from a CD or restore an item from trash, the icon for the file(s) have a lock emblem attached to it. I can still open it up and do what ever I want with it so it does not appear to be requiring root privileges.
I always have to do a chmod 777 in order for it to go away. Very annoying. Why does this happen (did not happen in any previous version) and what can I do to prevent it from happening?

---

### Post by mc4man on 2009-02-20
Whenever you transfer files from read only media or in case of the trash, location, the files are flagged as 'read only' 
There's no way around that, that I'm aware of, many ways to fix.

What i do is have a folder in home named fix where i transfer files to.
Then a simple *chmod -R +w fix*  (actually just set up a launcher to run the command.

---

