---
title: "finding files by attributes"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by A_M_S on 2010-10-22
Hello.

How can i find a file int the CLI using the attributes as the search criteria?

This could be useful to find bin files like the DOS  command  "dir *.exe"


Thanks

---

### Post by A_M_S on 2010-10-22
I found a solution 

It can be made with the command

find . -perm yxz 

Where xyz are the permission  codes

---

