---
title: "Metacity Buttons disappeared"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by AndyP79 on 2011-03-15
Hi Ya'll,
 Okay, here's the deal. I had addedd the Window applet buttons to the top panel and the appmenu. I am using 10.10
At a point, I have done away with all the panels and just using AWN. After removing the top panel, and even uninstalling the window applets, when I maximize a window, the metacity still disappears. I have been googling for an hour and can't seem to find a fix for this. I tried typing metacity --replace in the terminal, and that brings them back, but stops compiz, and then upon reboot, the metacity is back again? 
Any suggestions please?

---

### Post by andrewthomas on 2011-03-16
You either use metacity or compiz as a window manager, not both.  

Have you enabled window decorations in compiz?

---

### Post by matt_symes on 2011-03-16
Hi

Try..

```
gtk-window-decorator --replace
```

to replace. (If i understand you correctly)

Kind regards

---

