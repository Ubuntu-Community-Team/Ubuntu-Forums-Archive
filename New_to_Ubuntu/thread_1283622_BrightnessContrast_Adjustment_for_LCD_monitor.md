---
title: "Brightness/Contrast Adjustment for LCD monitor"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by infestor on 2009-10-05
is there a way in ubuntu to adjust your monitor brightness/contrast? i mean in system tray where always accessible. btw i use lenovo L 220xwc

---

### Post by freak42 on 2009-10-05
look for the brightness applet

---

### Post by infestor on 2009-10-05
> **freak42 said:**
> look for the brightness applet

how do find or install it?

---

### Post by freak42 on 2009-10-05
right click on your gnome panel where you want to add it choose "add to panel" then type brightness in the search box and it should show up.

---

### Post by infestor on 2009-10-05
> **freak42 said:**
> right click on your gnome panel where you want to add it choose "add to panel" then type brightness in the search box and it should show up.

it says it cannot retrieve information! i also dont use a laptop

---

### Post by infestor on 2009-10-10
any ideas?

---

### Post by freak42 on 2009-10-10
if you don't use a laptop, use your lcd's brightness/contrast buttons?

---

### Post by infestor on 2009-10-11
> **freak42 said:**
> if you don't use a laptop, use your lcd's brightness/contrast buttons?

yes i can do that but i was looking for a software solution for that.

---

### Post by bukzor on 2011-02-06
Try this:

```

xgamma -gamma .6

```

To get the same effect after restarting:


```

echo "xgamma -gamma .6" >> ~/.xsessionrc

```

---

### Post by s1baker on 2011-02-06
thanks bukzor!,
I have been looking for the past 2 months for something exactly like this as this old tube monitor that I am using won't
brighten enough. xgamma -gamma 1.3 makes it just about right.

---

### Post by malatesta on 2011-04-18
It works fine to me too! Thanks bukzor

---

### Post by B3taboy on 2012-12-23
> **bukzor said:**
> Try this:

```

xgamma -gamma .6

```

To get the same effect after restarting:


```

echo "xgamma -gamma .6" >> ~/.xsessionrc

```


I have created the file and added echo "xgamma -gamma .6" in  ~/.xsessionrc but seems that
doesn't work on lubuntu 12.10.
When typed in terminal it works but cannot make it persistent.

---

