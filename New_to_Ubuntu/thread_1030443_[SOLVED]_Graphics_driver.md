---
title: "[SOLVED] Graphics driver"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by garrydog on 2009-01-04
Hi
Just activated the ATI/AMD FGLRXT graphics driver ,rebooted I now have a black screen and "cannot display this video mode" can someone tell me how to get my monitor working again .
Thanks

---

### Post by stderr on 2009-01-04
Try switching to a TTY with Ctrl + Alt + F1. Login if necessary and try to execute

```
sudo aticonfig --initial
```

See if that helps (try rebooting). If not, try

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the questions.

---

