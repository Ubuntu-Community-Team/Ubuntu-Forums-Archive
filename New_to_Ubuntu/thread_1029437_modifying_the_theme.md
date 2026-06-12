---
title: "modifying the theme"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by stonecoldjha on 2009-01-03
hello everyone.
i am presently using the GTK theme "future" which has a dark panel as shown in the first screenshot.but,i want to use another panel image as panel background,so i right click on the panel,click properties,then background image and point it to a location,but the result is that the theme native panel style still dominates as is clear from the screenshot.so,how do i use my panel image fully?
the first screenshot shows the native theme panel.the other one shows what the panel is like when i try using a background image.

---

### Post by stonecoldjha on 2009-01-03
if it were possible to disable the contribution of this theme to the panel,this can be done.

---

### Post by AlexBellisBrown on 2009-01-03
I see the panel theme you have is basically transparent. Why dont you just change the bar to white/transparent? Might work and would look almost the same :)

---

### Post by stonecoldjha on 2009-01-03
but how?

---

### Post by AlexBellisBrown on 2009-01-03
Rightclick the panel, click properties, background tab select solid colour, change it to the colour you want a tint of, and move the bad between transparent and opaque. :) Close and youre done :)

---

### Post by stonecoldjha on 2009-01-03
i dont want to use a solid color but a background image.so that does not do the job.how can i disable the the contribution of the theme to the panel?

---

### Post by mcduck on 2009-01-03
Open the themes gtkrc file (you'll find it somewhere in /home/*username*/.themes/*nameofthetheme*) in text editor, and comment out the line 10 (include "panel.rc") by adding a "#" to the beginning of that line. That should pretty much remove all the changes that theme makes to your panels.

Depending on your theme/panel background/wallpaper you might also need to define new colors for text in your panels. You can do that by creating a file called ".gtkrc-2.0" in your home directory and pasting the following code there. (You can change the colors to whatever fits your desktop. Log out and back again to see the changes.)
```
style "panel"
{
fg[NORMAL] = "#000000"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"

style "panel-clock"
{
  fg[NORMAL] = "#000000"
}
widget "*.clock-applet-button.*" style "panel-clock"
```

---

### Post by stonecoldjha on 2009-01-03
thank you mcduck very much.it did the job very well.thank you so much again.

---

