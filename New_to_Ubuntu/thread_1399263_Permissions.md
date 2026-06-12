---
title: "Permissions"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by SirRedTooth on 2010-02-05
I have a webserver set up in /opt/lampp
I have already set permissions for the /lampp folder so everybody can open, edit and delete.
However when my webserver makes new files (which it very commonly does) it cannot edit them again in the future.

I would edit the permissions of the new file that the webserver makes but it would take ages to do them all individually.
Is there anyway to set the permissions for the folder, and all its sub-directories, including files made in the future.

---

### Post by Cabs21 on 2010-02-05
should be a small check box in the bottom left of the preferences tab that says apply changes to all sub-folders.

---

### Post by SirRedTooth on 2010-02-05
I think you mean the "Apply Permissions To Enclosed Files" button on the permissions tab (the preferences tab doesn't exist on properties.

Even when I do this, when new sub folders are created the same permissions don't seem to apply...

Maybe there is a terminal command for setting permissions to the /lampp folder and sub-folders to public editable that I can run. That would alleviate the problem temporarily....

---

### Post by SirRedTooth on 2010-02-05
I think i discovered the root of the problem.
When I change the setting for file access on the permissions tab and close then open the permissions tab the file access settings jump back to default.

Very annoying.

---

