---
title: "Remote Desktop Viewer won't startup"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by asharpham on 2010-04-08
When I click on Remote Desktop Viewer (Applications-->Other-->Remote Desktop Viewer) the program tries to start but then just gives up after about 10 seconds and doesn't open. Any idea how I can fix this?

---

### Post by tom.swartz07 on 2010-04-08
> **asharpham said:**
> When I click on Remote Desktop Viewer (Applications-->Other-->Remote Desktop Viewer) the program tries to start but then just gives up after about 10 seconds and doesn't open. Any idea how I can fix this?

Try running it from the terminal with a debug flag to see what's going on.

Assuming youre using the default program (vinagre), just open a terminal and type

```
vinagre
```
and let the program run.

It should post the errors if it crashes then, post them back here and we could go through it

---

### Post by asharpham on 2010-04-09
Yes that worked great. Thanks. I notice that the properties set for Remote Desktop Viewer in the menu had "vinagre -F %U". I'ver now removed the -F %U and it works like a charm.

---

