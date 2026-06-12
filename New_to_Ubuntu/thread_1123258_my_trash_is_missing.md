---
title: "my trash is missing"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by gkraju on 2009-04-12
hi i saw today my trash is missing i there any way i can get it back
thanks in advance

---

### Post by lisati on 2009-04-12
If you right-click on the bottom panel, then click "Add to panel", you should be able to get it back.

---

### Post by gkraju on 2009-04-12
> **lisati said:**
> If you right-click on the bottom panel, then click "Add to panel", you should be able to get it back.

thanks for your reply it gives me this error message 

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

---

### Post by lisati on 2009-04-12
> **gkraju said:**
> thanks for your reply it gives me this error message 

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

Hmmmm.... That's a new one on me. I'll have to "pass the reigns" to someone else.

---

### Post by sisco311 on 2009-04-12
Try to reinstall *gnome-applets* and restart the panel.

```
sudo apt-get install --reinstall gnome-applets
```
```
killall gnome-panel
```

---

### Post by gkraju on 2009-04-12
> **sisco311 said:**
> Try to reinstall *gnome-applets* and restart the panel.

```
sudo apt-get install --reinstall gnome-applets
```
```
killall gnome-panel
```

thanks it worked 
can you answer this thread 
[http://ubuntuforums.org/showthread.php?t=1123250]("http://ubuntuforums.org/showthread.php?t=1123250")
thanks in advance

---

