---
title: "rename computer"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-05-11
I reloaded my computer over the weekend because of an error that i created.  I noticed now though that in the router configuration page it says trinidad-laptop-pc how can i change that now?  when i reinstalled everything i made sure that it said user but that did not take effect.

---

### Post by roger_1960 on 2009-05-11
Hi

Try going to system-administration-network, then in the "general" tab unlock the screen with your password and change the host name.  I suspect you would have to reboot after this.

---

### Post by Iowan on 2009-05-11
Hopefully, the GUI will take care of changing everything that needs changed.   Otherwise, when changing the name manually, /etc/hostname and /etc/hosts need to both be changed - or **sudo** doesn't work right.

---

