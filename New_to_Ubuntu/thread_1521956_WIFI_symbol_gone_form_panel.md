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

### Post by s.fox on 2010-07-01
Hello,

I think you have removed the notification area from the panel.

Right click the top panel and choose "add to panel". Look for "notification area" and add it.

-Silver Fox

---

### Post by Daniel1994 on 2010-07-01
When this happens to me, I usually run

```
killall gnome-panel
```

and it comes back.

This will not work if you've removed the notification applet from your panel or something more serious.

---

