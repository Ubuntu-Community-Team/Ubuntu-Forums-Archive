---
title: "deleting files in opt folder"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by max00355 on 2010-12-04
i did rm than the path to the file but it still said there was no such path can someone help please

---

### Post by conradin on 2010-12-04
can you show us what you entered? maybe the last few lines of your bash history? has the file or folder been successfully removed?

---

### Post by asmoore82 on 2010-12-04
File paths and names with spaces or strange characters in them need to be escaped or quoted.

You could also ```
gksudo nautilus
``` to do some file administration graphically.

---

### Post by max00355 on 2010-12-05
this is exactly what i did in terminal

sudo rm /opt/altitude

and i said there is no such directory

---

