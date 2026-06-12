---
title: "Problem with trash can..."
date: 2010-06-16
forum: New to Ubuntu
---

### Post by camn on 2010-06-16
Okay... this is really important <_>
I was recovering pictures on an old desktop that BSOD'd by running the Ubuntu Live CD and putting them onto a memory key and putting them on a laptop... I accidentally sat on the keyboard which deleted the "Documents and settings" folder (it has Windows XP on it...) My question is, is there a way to restore stuff from the trash can without actually opening the folder for the trash can? Ever time I open it, it starts not responding... Help D:

---

### Post by Chesamo on 2010-06-16
Open Terminal. Enter the command ```
nautilus ~/.local/share/Trash/files/
``` That will open the Trash as a normal directory. NOTICE the period (.) before local.

---

