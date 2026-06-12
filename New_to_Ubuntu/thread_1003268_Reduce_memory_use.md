---
title: "Reduce memory use?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by DrMilo on 2008-12-05
I was browsing threads to find ways of improving performance in Ubuntu, Gnome and came across this command:

gconftool-2 -s /apps/metacity/general/reduced_resources -t bool true

Is this safe to run? What are the side effects? I'm running Hardy. Thanks in advance.

---

### Post by Diabolis on 2008-12-05
[http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/ch02s03.html](http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/ch02s03.html)

Its safe, it won't crash your system. You can use **gconf-editor** to do this too.

---

### Post by DrMilo on 2008-12-05
Thank you. I'll give that a try tomorrow.

Does it really improve performance?

---

