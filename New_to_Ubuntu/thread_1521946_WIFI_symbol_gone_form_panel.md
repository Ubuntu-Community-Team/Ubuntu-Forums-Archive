---
title: "WIFI symbol gone form panel"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by gordon33 on 2010-07-01
Hello

I am using 10.04 Ubuntu.

How do i get the WIFI symbol back on my Panel?

I logged on to my HP Laptop and their was a box asking if 
I wanted to keep some thing on my panel.  The big word in the box was Gnome.  I picked one of the 2 options and the box went awy. The next think I noticed was the WIFI symbol was not on my Panel. 

Gordon

---

### Post by cariboo on 2010-07-01
Open a terminal and type:

```
killall gnome-panel
```

To see if that corrects the problem.

---

