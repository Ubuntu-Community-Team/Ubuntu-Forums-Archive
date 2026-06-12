---
title: "Two themes at once??"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by justin43384 on 2010-11-19
After installing a new theme, I seem to be running two themes????
You can see in the screenshot that my appearance menu is different that what is seen...
I'm sorry the picture is a little messy

---

### Post by JustinR on 2010-11-19
Go to Applications > Accessories > Terminal:

```

nautilus -q

```

If that doesn't fix it try:
```

sudo killall gnome-settings-daemon
gnome-settings-daemon

```

---

