---
title: "ubuntu 8.10, black/beige screen after installation"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by ubuwiz on 2009-03-01
I successfully installed ubuntu 8.10. But when I log in with my username and password, I get a black screen. I can move the mouse around but I can't do anything. Prior to this installation I had ubuntu 7.04 installed without any problems. I even tried to install 7.04 back, but I had problems doing that as well. I don't remember what problem I had when reinstalling 7.04 but the 8.10 is definitely the black screen issue. Someone please save me from this frustration!!!!!!!!!!!!!!!

---

### Post by blueridgedog on 2009-03-02
Did your display work as expected while running the live CD?

You can try the following:

Press Ctr+Alt+F2 to bring up a terminal.  Log in with your user name and password, then enter:

```
sudo dpkg-reconfigure xserver-xorg
```

This will reconfigure your server.

---

