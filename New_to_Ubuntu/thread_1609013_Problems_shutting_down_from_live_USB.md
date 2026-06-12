---
title: "Problems shutting down from live USB"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Robert Buckmaster on 2010-10-29
When I boot my desktop from the live USB there is only one option when I press the shut down option: Suspend. But this doesn't shut down my computer; rather the screen comes back as before. So how you shut down?

---

### Post by Omnomnom on 2010-10-29
System > Preferences > Power Management > General > Click the drop down menu to make it say shut down > You might wanna install ubuntu properly so it saves you having to go back and keep changing the settings. And now, when you press the power button when it's on, it will turn it off!

---

### Post by beew on 2010-10-29
Seems to be a bug in the 10.10 live usb. You can add a shut down button that works to the panel by right clicking the panel and choose "add to panel", then on the menu choose the red button for shutting down. The default button  on the panel is white, it is part of the indicator applet or session applet or something like that, can't remember, so it is a part of the same applet that also displays the user name, but this red one is by itself.

---

### Post by Omnomnom on 2010-10-29
In 10.10 the shutdown applet opens the normal hibernate/sleep/shutdown/restart menu.

---

### Post by spcwingo on 2010-10-30
From a terminal:

```
sudo poweroff
```

---

