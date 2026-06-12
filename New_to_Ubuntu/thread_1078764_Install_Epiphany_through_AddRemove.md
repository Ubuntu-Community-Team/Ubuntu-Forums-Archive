---
title: "Install Epiphany through Add/Remove"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by ikisham on 2009-02-23
Sorry,..it's allright.

---

### Post by ptn107 on 2009-02-23
Indeed 'epiphany-browser' is a dummy package that will install 'epiphany-gecko' by default.  I would just do a:
```
sudo apt-get install epiphany-gecko
```
from the command line to install the browser.  You should have the appropriate icon under Applications -> Internet.

Edit: Come to think of it I don't have an icon either, hmm maybe install the webkit version (epiphany-webkit).

---

