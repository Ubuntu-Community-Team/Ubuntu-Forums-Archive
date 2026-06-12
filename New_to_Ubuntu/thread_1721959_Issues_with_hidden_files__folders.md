---
title: "Issues with hidden files / folders"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by IHeequ5i on 2011-04-05
I've a couple of questions regarding hidden files and folders.

1.  If I open my Home folder from the Places menu, I can use CTRL-H to display hidden files and folders.  I would like it to do this automatically. Can this be done?

2.  I was trying to install a program via PlayOnLinux and discovered that the installer can't "see" hidden files and folders.  Any way to fix this, or is that a PlayOnLinux question?

With regards to question 2, I did eventually figure out a way around my problem, so it's more of a curiosity thing now. But question 1 is something I'd like an answer to.

---

### Post by edm1 on 2011-04-05
For Q1: If you open nautilus and go to Edit>Preferences>View>'Show hidden and backup files' does this cause hidden files to be shown all the time?

---

### Post by wojox on 2011-04-05
1. Alt+F2 and type gconf-editor
Go to Apps > Desktop > Gnome > file_views > show_hidden_files

2. Don't know?

---

### Post by IHeequ5i on 2011-04-05
Thank you all for the swift responses.  I'm at work now, so I can't try these out.  Will post this evening with results.

---

### Post by IHeequ5i on 2011-04-05
Edit -> Preferences -> click the proper checkbox works very nicely for displaying my hidden files and folders.

Thank you very much.

---

