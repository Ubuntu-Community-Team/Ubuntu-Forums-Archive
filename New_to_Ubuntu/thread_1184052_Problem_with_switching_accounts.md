---
title: "Problem with switching accounts"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-06-10
I have 2 accounts A and B. A is the master account (not root) and B is a guest account. When I switch from A to B and try to use Cheese Webacam Booth, it logs me out and takes me to the log in screen for A!!

What am I doing wrong?

Thanks.

---

### Post by NightwishFan on 2009-06-10
Edit: I should ask. Is it just not logging in? Or does Cheese cause you to log out?

Try this:

Press Alt+f2 and type:
```
gstreamer-properties
```
Press enter.

Under video settings change it to x11video. (I think its x11 video).

See if that works. If so, then the Xvideo extension on your GPU was causing X to crash. If not, then change it back to the default, likely Xvideo.

---

### Post by dunbrokin on 2009-06-10
> **NightwishFan said:**
> Edit: I should ask. Is it just not logging in? Or does Cheese cause you to log out?

Try this:

Press Alt+f2 and type:
```
gstreamer-properties
```
Press enter.

Under video settings change it to x11video. (I think its x11 video).

.
Tried that (thanks) ...did not work...

---

### Post by dunbrokin on 2009-06-12
Actually, you are right..the X11 did not work ...but one of the other choices did.

Thanks.

---

