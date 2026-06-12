---
title: "main toolbar home folder"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by robalcorn on 2010-11-19
Could someone please tell me how to get the toolbars back and navigation arrows back when opening home folder or documents etc?

---

### Post by 101011010010 on 2010-11-19
Hello.
There's an option in "gconf-editor" that should help.
Press Alt+F2 and type or copy "gconf-editor" (without the "")
Navigate to: > /apps/nautilus/preferences/start_with_toolbarAdd the Tick and every thing should be back to normal.
I hope this helps.

---

### Post by asmoore82 on 2010-11-19
Have you enabled "spatial" browsing mode?

If so, open your Home folder,
then "Edit -> Preferences",
Click the "Behavior Tab",
Uncheck "Open each folder in its own window."

---

