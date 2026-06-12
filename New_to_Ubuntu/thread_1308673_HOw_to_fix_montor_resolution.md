---
title: "HOw to fix montor resolution"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by PhilMan9045 on 2009-10-31
I just installed Ubuntu Karmic Koala and I'm using a 20 inch Samsung monitor but i'm getting crappy resolution. How do I fix this?

---

### Post by Oropher8598 on 2009-10-31
If you're using proprietary graphics drivers, you may be able to fix it from the settings app they provide.. otherwise you'll probably have to edit /etc/X11/xorg.conf

Hmm... I don't have a link for a 'how to'... anyone else?

---

### Post by cariboo on 2009-10-31
If you are using an Nvidia graphics adapter, open a terminal and type:

```
nvidia-xconfig
```

The above command will create a new /etc/X11/xorg.conf file. Once finished reboot the computer.

---

### Post by PhilMan9045 on 2009-10-31
I figured it our somehow. Thanks

---

