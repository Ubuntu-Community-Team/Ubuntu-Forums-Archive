---
title: "[SOLVED] empathy/pidgin and other programs dont detect wvdial .."
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by da.tiger on 2008-10-12
I am connecting to the net using wvdial, and a few programs dont detect it.. how do i fix this >

---

### Post by da.tiger on 2008-10-13
found it myself, just disable the network manager :)

---

### Post by Rhubarb on 2009-12-21
It's also possible to get empathy working again without disabling network manager:-

```
gconf-editor
```

Then go into:
apps --> empathy

Then uncheck the box "use_conn"

Close the gconf-editor, then run empathy as usual :)

I'd found this solution from:
[http://www.mail-archive.com/ubuntu-in@lists.ubuntu.com/msg06339.html](http://www.mail-archive.com/ubuntu-in@lists.ubuntu.com/msg06339.html)

---

### Post by omkardanke on 2010-02-09
Thanks. Works like a charm.

---

### Post by ridowan007 on 2010-04-04
For pidgin type ```
pidgin -f
```
in a terminal. Should be work.

---

