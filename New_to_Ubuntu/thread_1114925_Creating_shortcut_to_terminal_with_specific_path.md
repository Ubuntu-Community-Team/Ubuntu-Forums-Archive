---
title: "Creating shortcut to terminal with specific path"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by nibo01 on 2009-04-03
Hi all!

How do I create a batch script which starts up the terminal and changes to a specific directory?

This is what I have so far:
#!/bin/bash
cd /usr/bin/gnome-terminal --working-directory=/home/admin/

But the script exits the window. I want the terminal window to stay open with that path.

Thanks!

---

### Post by freak42 on 2009-04-03
try
```
#!/bin/bash
/usr/bin/gnome-terminal --working-directory=/home/
```

without the cd command

---

### Post by nibo01 on 2009-04-03
works like a charm, thx!

---

### Post by freak42 on 2009-04-03
oh

btw.. I removed the ..admin/ part of the path.. because I don't have such a directory.. and I wanted to test it..

but I guess you got that fixed..

---

