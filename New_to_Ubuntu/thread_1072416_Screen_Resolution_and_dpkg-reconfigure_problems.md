---
title: "Screen Resolution and dpkg-reconfigure problems"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by kakshmire on 2009-02-17
Hi guys. I'm quite new to this so sorry if this makes not much sense or I don't know what I'm talking about... This seems like a pretty common problem of the screen resolution being stuck on a low setting (which mine is). I've read around as much as I can find and would I be right to be trying to run this in the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It seems to go to all sorts of delicious options except when I run that I just get this appear in the terminal

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090217150717
```

Dunno what I'm doing wrong (or right for that matter) but any help would be massively appreciated.

Cheers

---

### Post by insineratehymn on 2009-02-17
Try xrandr, as long as your gui works that may get you a bit further.

---

### Post by kakshmire on 2009-02-17
Thanks for the reply, I've just tried it, but it only gives me the same options that are available from the system preferences menu...

---

### Post by insineratehymn on 2009-02-17
Wanna post your xorg.conf file?

```
cat /etc/X11/xorg.conf
```

---

