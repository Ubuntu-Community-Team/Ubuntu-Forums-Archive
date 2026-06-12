---
title: "Volume panel gone, cannot add"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by Pikzilla on 2009-12-22
One day, I found I had two volume controls right next to each other. I tried deleting one, but both were deleted. There is no option to add it in the "Add to panel" menu. What the hell happened?

---

### Post by Moshanator on 2009-12-22
Try typing this into terminal:
```
gnome-volume-control-applet
```

---

### Post by Pikzilla on 2009-12-22
** (gnome-volume-control-applet:8992): WARNING **: Applet is already running, exiting

---

### Post by tilixibr on 2009-12-22
did you try logging out and logging back in?

---

### Post by wojox on 2009-12-22
Add "Notification Area" in "Add to Panel".

---

### Post by Pikzilla on 2009-12-23
Thanks, that worked, Wojox!

---

### Post by sbelz79 on 2009-12-23
> **wojox said:**
> Add "Notification Area" in "Add to Panel".

I was having the same problem- this solved it.  Thanks!

---

### Post by sbelz79 on 2009-12-23
> **Pikzilla said:**
> One day, I found I had two volume controls right next to each other. I tried deleting one, but both were deleted. There is no option to add it in the "Add to panel" menu. What the hell happened?

That's exactly what happened to me! (adding notification area, above, solved the problem)

---

