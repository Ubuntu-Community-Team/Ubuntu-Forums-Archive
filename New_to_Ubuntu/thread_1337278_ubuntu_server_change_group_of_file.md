---
title: "ubuntu server change group of file"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by abraves247 on 2009-11-25
I am running ubuntu server with no gui and i am trying to figure out how to add two groups i have created to both have permissions to open the folder but no one else.
 
I have tried the chown command but I think I am not entering in the command right becasue only one group has permissions to open the folder

---

### Post by mikewhatever on 2009-11-25
I'd rather use chmod:

sudo chmod g+r group-name  -  that should give group-name read access.

---

