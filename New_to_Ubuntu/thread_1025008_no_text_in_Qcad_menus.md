---
title: "no text in Qcad menus"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by scotttie on 2008-12-29
Hi,
added qcad to my system, but the text is missing off the menus, the underscore is there and when you run the mouse over the area you very briefly see the text (too fast to read).
any help greatly appreciated,
thanks
Scottie

---

### Post by scotttie on 2008-12-29
bump

---

### Post by aracosta on 2009-01-04
Check the Bug #300719. the solution worked for me.

[https://bugs.launchpad.net/ubuntu/+bug/300719](https://bugs.launchpad.net/ubuntu/+bug/300719)

Try adding:
Option "RenderAccel" "False"

---

