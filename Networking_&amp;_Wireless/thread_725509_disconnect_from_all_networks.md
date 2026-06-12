---
title: "disconnect from all networks"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by perito on 2008-03-15
how do i disconnect from all networks after ive connected to one?

---

### Post by mssever on 2008-03-15
Your question is a bit vague. Does this help?

```
sudo /etc/init.d/networking stop
```
(change stop to start to reenable)

---

### Post by perito on 2008-03-16
that does the trick, but I noticed that on the right corner up it still says (connected to MyConnection)
though I shouldnt be connected since I stopped networking ?
why is that?

---

### Post by mssever on 2008-03-16
> **perito said:**
> that does the trick, but I noticed that on the right corner up it still says (connected to MyConnection)
though I shouldnt be connected since I stopped networking ?
why is that?

Probably nm-applet never updated its status. If you right click on it, there's an Enable Networking item. You can try that and see if it works.

---

