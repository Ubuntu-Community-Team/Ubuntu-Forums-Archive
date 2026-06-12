---
title: "dpkg -i *.deb execution sequence"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by KurtRao on 2010-03-04
Hi,

I'm using "dpkg -i *.deb" to install packages but I have a question, if A.deb depends on B.deb (and no other dependencies), will B.deb be installed before A.deb is installed? I can make sure both A.deb and B.deb are under the same directory.

Thanks a lot!
Kurt

---

### Post by nothingspecial on 2010-03-04
1 I think it would be better to install one by one, I don`t think dpkg is that clever.

2 If B is supposed to go in /usr/lib then A will look for it there even if A is in /usr/bin if you see what I mean. Just let them go where they go.

---

