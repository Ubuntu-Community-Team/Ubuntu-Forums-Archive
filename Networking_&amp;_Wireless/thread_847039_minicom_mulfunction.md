---
title: "minicom mulfunction"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by pingdoc on 2008-07-02
hi evry1, i have a problem with my minicom. wheneva i connect a router,it comes on but with funny shapes and signs all over the screen.what could be the problem?

---

### Post by Rhubarb on 2008-07-02
Not entirely sure, it could be incorrect baud rate / flow control perhaps.
You could try installing gtkterm from the repositories (which may help, it's an alternative to minicom):
```
sudo aptidude install gtkterm
```
You'll find it in Applications --> Accessories --> Serial port terminal

---

