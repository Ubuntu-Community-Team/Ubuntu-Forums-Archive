---
title: "Prevent ~ backup files"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Mariane on 2010-07-12
Whenever I modify a file a ~ backup file is immediately created. This is annoying when I work on some code because I use grep a lot. For example I do
grep -R variablename *
to see all the places where the variable "variablename" appears. 

The ~ files make the corresponding lines appear twice, and the list is sometimes long enough without this. And regularly cleaning the folder by deleting the ~ files is a bit tedious. 

Where are the settings to say I don't want ~ files to be created, please? 

Mariane

---

### Post by mike555 on 2010-07-12
In Gedit, go to Edit->Preferences->Editor, and then uncheck the box labeled, "Create a backup copy of files before saving.

---

### Post by Mariane on 2010-07-14
Thank you. I was looking for general settings, I didn't know they were program-specific. 

For Kwrite I found it at:
Settings
Configure editor
Open/Save
Advanced
Backup on save
Local files

Mariane

---

