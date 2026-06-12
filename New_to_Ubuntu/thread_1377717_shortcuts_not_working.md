---
title: "shortcuts not working"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Matt26 on 2010-01-10
i have a number of shortcuts for local and remote NTFS volumes that i have placed on the top bar of my screen (where the applications, places and system menus reside) by dragging them from the Computer location to the bar.

when i click on them i get an error message similar to this:
> Could not open location 'computer:///40%20GB%20Hard%20Disk.drive'

No application is registered as handling this file

i'm not sure what exactly the issue is since i have made these types of shortcuts in the same place before.

any ideas as to how i can fix this?

i'm using ubuntu 9.10.

---

### Post by cariboo on 2010-01-10
Replace the %20 with \ to see if that makes a difference.

---

### Post by Matt26 on 2010-01-12
> **cariboo907 said:**
> Replace the %20 with \ to see if that makes a difference.

correct me if i'm wrong here, but doesn't %20 represent a space-   in this case, 'computer:///40 GB Hard Disk.drive'?

i'm almost certain that i was able to create these types of shortcuts the same way in earlier versions of ubuntu and they worked fine... provided my memory serves me correctly, what has changed?

is there another way to create the shortcuts?  i've tried using different options via the bar's context menu (using Add to panel) but i haven't been successful yet.

---

### Post by Matt26 on 2010-01-14
for anyone who is interested, this can be fixed by setting the Command field in the Properties of the shortcut to *file:///path/to/directory*

---

