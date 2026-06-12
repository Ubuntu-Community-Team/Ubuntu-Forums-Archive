---
title: "Start Bar Oddities"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by t0rment2004 on 2011-03-10
[http://img14.imageshack.us/img14/5388/screenshot1yb.png](http://img14.imageshack.us/img14/5388/screenshot1yb.png)

Start bar has two dates on it and multiple things I've stopped using but remain on the bar and can't be removed.

What kind of terminal work do I have to learn now?

---

### Post by maqtanim on 2011-03-10
Run the following command
```
killall gnome-panel
```

---

### Post by t0rment2004 on 2011-03-10
That didn't work. It still looks just like the picture.

---

### Post by Matt__ on 2011-03-10
try these in the terminal one after the other.

```
gconftool &#8211;-recursive-unset /apps/panel
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

this should reset your top and bottom panels to default.

---

### Post by t0rment2004 on 2011-03-10
That worked, thanks.

---

