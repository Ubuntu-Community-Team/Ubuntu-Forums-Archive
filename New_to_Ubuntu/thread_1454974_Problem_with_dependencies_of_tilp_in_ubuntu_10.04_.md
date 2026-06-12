---
title: "Problem with dependencies of tilp in ubuntu 10.04 (beta 2("
date: 2010-04-15
forum: New to Ubuntu
---

### Post by nene7 on 2010-04-15
hi i want to install the Tilp for connect my ti-89 graphic calculator but i first tried in ubuntu software center and it say that Package dependencies cannot be resolved, tilp2 are in details. Then i tried to install package tilp2 from sypnatic but appear:

PD: Dell inspiron 6400 with ubuntu 10.04 (beta 2).

---

### Post by bwhite82 on 2010-04-15
Dependency errors can sometimes be frustrating. Thankfully, Debian-based distros have builtin functionality for this issue. Drop to a terminal and type in:

> sudo apt-get -f install

Then try installing your program again.

---

### Post by oldos2er on 2010-04-15
Check System, Administration, Software Sources, and make sure the universe repository is enabled.

---

### Post by nene7 on 2010-04-15
[oldos2er]("http://ubuntuforums.org/member.php?u=338320") how i know and how i enable the universal repositories.

---

### Post by oldos2er on 2010-04-15
Again, check the menus System, Administration, Software Sources. Make sure all the boxes are checked.

---

### Post by slavSan on 2010-06-05
Thanks very much about the tip. I had this problem with 10.04 and you helped me fix it. Don't know how the updates from ubuntu (the main ones) turned off themselves. They were turned on some days ago, I'm sure about that. Anyways here I found the solution. Thanks again.

---

