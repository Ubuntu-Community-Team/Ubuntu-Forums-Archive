---
title: "etc/init.d/rc post standard contents please"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by evrkusd on 2009-02-09
hi,
changed my init.d/rc file and still works but want to change it back to what it was. can someone post there file contents?
thanks a lot.

---

### Post by llamakc on 2009-02-09
You should declare which version of Ubuntu you are using.

You can also figure out which package a file is provided by like this:

```

dpkg -S /etc/init.d/rc

```

Which on 8.10 results in:

```

ken@llamakc 06:24:43:/etc/init.d$  dpkg -S /etc/init.d/rc
**sysv-rc**: /etc/init.d/rc

```

---

### Post by evrkusd on 2009-02-09
sorry yeah 8.10 intrepid

---

### Post by snova on 2009-02-09
You could try:

```
sudo aptitude reinstall sysv-rc
```

Based on llamakc's post.

---

