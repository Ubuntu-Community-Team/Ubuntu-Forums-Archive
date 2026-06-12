---
title: "how can i get rid of my status indicator (and ubuntu one thingy) in panel?"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-28
I want to get rid of this thing. How?

---

### Post by mike555 on 2010-05-28
right click and remove , but you will loose your volume icon  , so make sure it's turned up where you want it ..

---

### Post by lsk3993 on 2010-05-28
Oh and just in case you want to restore it all later, this is useful:
> gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by lsk3993 on 2010-05-28
> **mike555 said:**
> right click and remove , but you will loose your volume icon  , so make sure it's turned up where you want it ..
Also, why would removing the status thing remove the volume control? Those should be separate right? They are for me at least...

---

### Post by Elfy on 2010-05-28
I think that is the indicator-me package - remove that from synaptic - might need a logout/login

Edit - checked - I do not have that installed - I removed the same thing

---

