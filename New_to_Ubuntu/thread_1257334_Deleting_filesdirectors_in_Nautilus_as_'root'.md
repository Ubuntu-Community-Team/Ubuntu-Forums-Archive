---
title: "Deleting files/directors in Nautilus as 'root'"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Zer0Nin3r on 2009-09-03
Question:  If I launch nautilus from the command line using the sudo command, what happens to files I delete using the 'delete' key on my keyboard VS shift+del?

I noticed there isn't a trash can for the root user, is that correct?  Does the file get stored in a "trash" somewhere else?

---

### Post by wojox on 2009-09-03
Look in /root/.Trash/

---

### Post by sisco311 on 2009-09-03
the location of the trash is ~/.local/share/Trash/ where ~ is the home directory of the user. 

files deleted as root should go in /root/.local/share/Trash/files

---

### Post by Zer0Nin3r on 2009-09-03
> **sisco311 said:**
> the location of the trash is ~/.local/share/Trash/ where ~ is the home directory of the user. 

files deleted as root should go in /root/.local/share/Trash/files

Thank you for the reply, unfortunately that directory doesn't exist.

> **wojox said:**
> Look in /root/.Trash/

Thank you for the reply as well.  You answered my question sufficiently.  It's good to know so you don't end up with wasted space.

---

### Post by nmaster on 2009-09-03
btw, you should run Nautilus as root with "gksudo nautilus" 

gksudo is safer for graphical applications.

---

### Post by julgic23 on 2012-03-06
thanks Nmaster.... I got it right now...

---

