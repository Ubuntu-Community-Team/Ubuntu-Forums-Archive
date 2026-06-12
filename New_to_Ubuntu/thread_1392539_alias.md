---
title: "alias"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by Drenriza on 2010-01-28
When i make an alias command, when i then close and open the terminal. The newly added command will be removed/deleted. How can i save the alias i make?

Thanks on advance.

EDIT:
How can you remove an alias again?

---

### Post by ICEB3AR on 2010-01-28
edit ~/.bashrc and add in the file your alias command
e.g.

alias ll ='ls -l'

to remove you only uncomment or delete your specified alias-command in the file.

---

