---
title: "Wireless help"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by te00646 on 2009-11-09
I am very new to ubuntu. I just installed ubuntu 9.1 on my laptop. I can't figure out how to connect to wireless. When I look I can't even see a network to connect to. I am an extreme begineer and need help. Thanks

---

### Post by original_jamingrit on 2009-11-09
It might be that you have an unsupported wireless card.  But all is not lost.  There are ways to make them work.

Open Terminal found under Applications->Accessories, and enter the following command:
```
lspci
```

and post the output here.  It will tell us what type of wireless card you have, and then we can tell you what to do next.

EDIT:  the command might actually require sudo, as in
```
sudo lspci
```

---

