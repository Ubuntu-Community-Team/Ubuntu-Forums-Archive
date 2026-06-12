---
title: "No desktop"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by undo123 on 2011-06-16
[SIZE=3]I have had my motherboard fail so have reinstalled the old one but now when I start Ubuntu all I get is a black screen and a login. when I log in and enter my password I still just get a black screen. How do I get back to my desktop.

James.[/SIZE]

---

### Post by manzdagratiano on 2011-06-16
If you changed your motherboard, you probably have different hardware, whereas you have drivers for the wrong hardware now. You should boot from a LiveCD, backup your /home and other data, and reinstall Ubuntu.

EDIT: I thought you had no login whatsoever. If you can log into text mode, you should be able to reconfigure X:
```

$ sudo dpkg-reconfigure xserver-xorg

```
and see if that gives you a working X.
BUT, I suspect you might have more trouble if too much hardware has changed, unless you reinstall.

---

