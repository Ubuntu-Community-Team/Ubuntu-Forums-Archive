---
title: "Edit Screen Resolution command?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by seedlings on 2009-01-18
I finally got 1024x768 working, then <idiot> clicked one resolution higher.  Bad idea.  The monitor went to "OUT OF RANGE" and now I can hear ubuntu load, but can't see anything.

Ctrl-alt-F2 and I can see to enter commands.

So, I need to know what command to enter to tell the nvidia geforce4 card to go back to 1024x768.

As always, thanks again!

---

### Post by blueridgedog on 2009-01-18
At the terminal prompt, you can reconfigure the x server with:

```
sudo dpkg-reconfigure xserver-xorg
```

---

