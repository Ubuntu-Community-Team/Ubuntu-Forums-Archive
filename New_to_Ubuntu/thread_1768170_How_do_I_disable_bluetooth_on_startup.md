---
title: "How do I disable bluetooth on startup?"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by kyletstrand on 2011-05-26
I noticed that Bluetooth automatically starts when I boot up ubuntu. I never use it and have no intention of ever using Bluetooth.  

How can I disable Bluetooth from automatically starting up when my system starts up?

Thanks in advance :)

---

### Post by spillage2 on 2011-05-26
system-presences-startup applications and uncheck bluetooth should do it I think...

spill

---

### Post by audiomick on 2011-05-26
Yep, that should do it. Except that it is "preferences", not "presences"... ;)

---

### Post by kyletstrand on 2011-05-26
Thanks, got it!

---

### Post by spillage2 on 2011-05-26
lol its been one of those days....

---

### Post by einov on 2011-10-18
How can I do this in the new 11.10? They say bluetooth eats up battery and since I don't use bluetooth I'd like to disable it.

---

### Post by howefield on 2011-10-18
Pretty much the same way, click on the Dash and search for Startup Applications and uncheck Bluetooth.

You might meed to run these two terminal commands first to get the startup applications to show up...

```
cd /etc/xdg/autostart/
```

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

