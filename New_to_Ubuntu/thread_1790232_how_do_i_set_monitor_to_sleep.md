---
title: "how do i set monitor to sleep"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by telltom on 2011-06-24
In Xubuntu 10.04 I can't seem to find the setting to force the monitor to turn off, such as if idle for 10 minutes? thanks tom

---

### Post by trizrK on 2011-06-24
Go to System>Preferences>Power Management and adjust the settings to how you want it.

---

### Post by telltom on 2011-06-24
thanks i did but i set it for 10 minutes and it remains on. I'm now choosing no screensave to see if that is what is stopping if from going off.

---

### Post by telltom on 2011-06-28
no, still not working. any ideas?

---

### Post by Toz on 2011-06-28
Is xfce4-power-manager running? Open a terminal window, type in the following, and post back the results.
```
ps -ef | grep xfce4-power | grep -v grep
```

What make/model of monitor do you have?

---

