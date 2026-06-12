---
title: "cannot delete a folder"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Matt26 on 2009-04-01
i can't delete a folder that has some empty sub-directories..

from the command prompt when i use ```
sudo rm -rf /dir
``` i get

[B]rm: cannot remove directory `/dir': Directory not empty
[/B]

if i start nautilus with root permissions using ```
gksudo nautilus
``` i get a graphical version of the same error.

any ideas?

---

### Post by alphacrucis2 on 2009-04-01
> **Matt26 said:**
> i can't delete a folder that has some empty sub-directories..

from the command prompt when i use ```
sudo rm -rf /dir
``` i get

[B]rm: cannot remove directory `/dir': Directory not empty
[/B]

if i start nautilus with root permissions using ```
gksudo nautilus
``` i get a graphical version of the same error.

any ideas?

Did you check for hidden files?

---

### Post by SuperSonic4 on 2009-04-01
It wouldn't matter?

It could contain an essential system file?

---

### Post by Matt26 on 2009-04-01
there are no system files, nothing related to ubuntu..

how do i remove the folder?

---

### Post by MasterNetra on 2009-04-01
whats the permissions of the dir folder, and who is set as owner? otherwise if its just the folder and you can't delete it then lock it up so no one can access it or do anything with it. It won't hurt your system to keep it and if someone hacks your system it be amusing if they spend a lot of time trying to break into just to find nothing. :lolflag:

---

### Post by aesis05401 on 2009-04-02
I believe you will get this error if you do not have read permission for all subdirectories as the subdirectories are enumerated - or 'read' - prior to deleting. 

I would be interested to hear if this is a permissions problem.

Edit: Wikipedia says read write execute for all subdirectories, and mentions the directory not empty thing with regards to lack of perms for a subdirectory item.

---

### Post by mocoloco on 2009-04-02
Very strange.  Can you remove any of the empty subdirectories?  Maybe one of them in particular is the cause?
As far as I know, as root you should be able to trash anything, even important stuff like /var or /proc, though I've never tried that myself :)

---

### Post by Matt26 on 2009-04-02
a system restart fixed the issue..

---

