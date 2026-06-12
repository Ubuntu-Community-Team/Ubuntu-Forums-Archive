---
title: "vnc don't allow low colors"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by gcbzzzz on 2008-06-15
I have remote connections enabled in the ubuntu UI.

I connect from home to work. and on previous ubuntu versions i specified -depth 8 and everything was perfect.

now both computers upgraded to ubuntu 8.04, and now vnc refuses to do less then true color. which is the same as having my work wall paper from work visible at home, as the network use is so heavy that almost no click or key press happens on the other end.

I already tried installing the old viewer. and using -depth 8 and -quality 0. none helped in any way.

don't know if relevant, but i have desktop effects enabled on the host and client.

---

### Post by gcbzzzz on 2008-06-15
```
vncviewer -quality 0 -compresslevel 9
```

that did the trick. but is almost unreadable. -dept 8 was immeasurably better

---

