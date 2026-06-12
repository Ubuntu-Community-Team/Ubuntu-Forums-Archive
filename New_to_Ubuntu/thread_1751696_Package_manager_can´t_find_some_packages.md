---
title: "Package manager can´t find some packages"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by kingcu on 2011-05-06
When trying to install phpMyAdmin, the package manager downloaded a dozen or so packages OK, but failed on a few of them, which all resides on security.ubuntu.com domain. An example:

```
Failed to fetch http://security.ubuntu.com/pool/main/p/php5/php5-common_5.3.2-lubuntu4.7_amd64.deb
   404 Not Found [IP: 91.189.92.166 80]
```

What should I do in this case? Please help.

---

### Post by wilee-nilee on 2011-05-06
> **kingcu said:**
> When trying to install phpMyAdmin, the package manager downloaded a dozen or so packages OK, but failed on a few of them, which all resides on security.ubuntu.com domain. An example:

```
Failed to fetch http://security.ubuntu.com/pool/main/p/php5/php5-common_5.3.2-lubuntu4.7_amd64.deb
   404 Not Found [IP: 91.189.92.166 80]
```

What should I do in this case? Please help.

Open synaptic find the package right click on it for missing or needed dependencies, recommended installs etc.

---

### Post by kingcu on 2011-05-07
sorry, but could you be more specific? Thanks.

---

### Post by wilee-nilee on 2011-05-07
> **kingcu said:**
> sorry, but could you be more specific? Thanks.

In synaptic there is a search bar type in your install candidate phpMyAdmin, when you see it come up right click on it and look at the stuff, it will probably tell you exactly what your missing.

Synaptic, is in the menu.

---

### Post by kingcu on 2011-05-07
Yeah, that part I know. The problem is that Synaptic cannot download the missing packages. How to fix that?

---

