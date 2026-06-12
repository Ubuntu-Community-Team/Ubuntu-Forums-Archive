---
title: "remaining memory"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by kmgraham on 2010-05-30
how do I see how much memory I have left on my laptop?

---

### Post by mikewhatever on 2010-05-30
System->Admin->System Monitor.
You can also use **free -m**.

---

### Post by nhasian on 2010-05-30
> **kmgraham said:**
> how do I see how much memory I have left on my laptop?

when you say memory we think of ram.  a lot of people get that mixed up with hard disk space.  If you want to see how much hard disk space you have left, you can also see that in the System Monitor under the File Systems tab.  alternatively in a terminal you can type:

```
df -h
```

you may also like to use the [disk space screenlet]("http://gnome-look.org/content/show.php/Disk+Space+Screenlet?content=70718"):

[IMG]http://gnome-look.org/CONTENT/content-pre1/70718-1.png[/IMG]

---

### Post by kmgraham on 2010-05-30
Thank you, that was helpful, I am very new to Ubuntu so am just feeling my way around

---

