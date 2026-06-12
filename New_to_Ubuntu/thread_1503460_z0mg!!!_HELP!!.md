---
title: "z0mg!!! HELP!!"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by fremantle on 2010-06-06
i deleted BOTH of my gnome panels (uppr one and the lower one)


how do i get them back (with mayb default settings)

---

### Post by TriBlox6432 on 2010-06-06
You actually can't delete both, it won't let you...  :confused:

---

### Post by fremantle on 2010-06-06
well it did!!! :(:(

---

### Post by wojox on 2010-06-06
Run these two commands in the terminal:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

---

### Post by fremantle on 2010-06-06
> **wojox said:**
> run these two commands in the terminal:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```
[color="red"]**[b]i love you**[/b][/color]

---

### Post by fremantle on 2010-06-06
but i have 1 more prob

---

### Post by wojox on 2010-06-06
> **fremantle said:**
> but i have 1 more prob

Yes.....

---

### Post by sille777 on 2010-06-06
> **wojox said:**
> Run these two commands in the terminal:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

that code saved my bacon a couple weeks ago.  You're Not the first one to accidentally remove the top panel

---

