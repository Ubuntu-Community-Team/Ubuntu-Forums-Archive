---
title: "Lost  Panel item"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by bob brazie on 2010-10-15
I have been fooling around with 10.10 and have somehow deleted the item that has the Evolution calendar and the weather items. 

Could someone help me restore it? I can't seem to find it in the "add to panel".

Thanks in advance. Bob.

---

### Post by AndyM3 on 2010-10-15
Are you talking about the Clock applet?

---

### Post by andrewthomas on 2010-10-15
If you just deleted it from your panel.  Then you can 

```
rm -r ~/.gconf/apps/panel
```

To restore your gnome-panel to the default settings

---

### Post by bob brazie on 2010-10-15
Is that the one to add to be able to click on it to see the Evolution calendar?

---

### Post by AndyM3 on 2010-10-15
Yes, I believe the Clock applet shows Evolution appointments on clicking. It also shows the weather.

---

### Post by mathay on 2010-10-15
Yes, it does show the weather and the calender.

If you'd prefer, you could just right click the panel, click "Add to panel..." and then click and highlight the "Clock" option. Then click "Add." That should re-add the clock, weather and calender panel item.

andrewthomas' idea is good too. It will help you familiarize yourself with the terminal.

---

### Post by bob brazie on 2010-10-15
That was the one!! Thanks to all. Bob.

---

