---
title: "user interface"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by pgrim91 on 2011-09-02
So I have Ubuntu 11.04 and my friend has 10.04.  Basically, I want to get rid of all the things that make it look like a mac in the new one (expand, minimize, and close commands on the left of windows, the unity dock thing on the left, etc).  How do you change or configure these visual elements?

---

### Post by kansasnoob on 2011-09-02
[http://ubuntuforums.org/showthread.php?t=1718631](http://ubuntuforums.org/showthread.php?t=1718631)

Changing button order:

Best to choose another theme but if you must:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

This will not work with 11.10!

---

### Post by grahammechanical on 2011-09-02
So you do not like the UI in 11.04? The Unity interface is not going to go away. Ubuntu 11.10 is based on Gnome 3. And the alternative to the Unity UI is the Gnome 3 shell. See what it looks like.

[http://www.gnome.org/gnome-3/]("http://www.gnome.org/gnome-3/")

Similar to what we already have with 11.04. Yes? It remains to be seen if it will be possible to progress using Gnome 3 and also have the usual desktop look that has been around for decades.

Regards.

---

### Post by Old_Grey_Wolf on 2011-09-02
> **pgrim91 said:**
> How do you change or configure these visual elements?

To change to traditional Gnome, logout and then after clicking on your username, select Ubuntu Classic Desktop from the options at the bottom of the login screen.

---

