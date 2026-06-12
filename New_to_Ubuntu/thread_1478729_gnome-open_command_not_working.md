---
title: "gnome-open command not working"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by fudgynubbles on 2010-05-10
Hi, I'm a Ubuntu n00b, and I'm trying to learn how to use the command line more efficiently. I used the command "gnome-open" to open a video file successfully using the terminal program found in the GUI, but when I try it using the "ctrl-alt-F2" terminal it gives the error:

"GConf Error: Failed to contact configuration server; some possible causes are ..."

This happens in that terminal no matter what I try to open. Why doesn't it work? Thanks in advance.

---

### Post by ankspo71 on 2010-05-10
That is because ctrl-alt-F2 is a non graphical environment (command line only). Those types of terminals (better known as ttys) are mainly used for repairs and such. Using things like "nano" (a command line text editor) will work there though.

---

