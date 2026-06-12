---
title: "internet connection"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by arvindenrique on 2008-01-02
should i run the command SUDO PPPOECONF everytime i start my computer to browse?
during configuration i ve set it to run at the startup but still it requires me to run the command every time.

---

### Post by ray bot on 2008-01-02
pppoeconf is for configuring a pppoe connection, and should only need to be run once.  Once it has been configured, you should be able to connect with ```
pon dsl-provider
```

---

