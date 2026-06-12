---
title: "Starting another xorg/xserver"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Dark Aspect on 2009-06-11
Hello,

Whats the best way to start another xserver on Ubuntu? I have used xinit -- :1 in tty1 (what you get when you press Ctrl+Alt+F1) but the audio under that xorg seems to be linked to the first xserver. In other words I can't go between the two desktops without serious audio issues, is there another way I can accomplish this without using xinit or perhaps a better way?

---

### Post by blueridgedog on 2009-06-12
Here is a tutorial that I found while searching:

[http://www.justlinux.com/nhf/X_Window/Creating_Multiple_GDM_Logins_on_a_Single_Workstation.html](http://www.justlinux.com/nhf/X_Window/Creating_Multiple_GDM_Logins_on_a_Single_Workstation.html)

---

### Post by Dark Aspect on 2009-06-12
> **blueridgedog said:**
> Here is a tutorial that I found while searching:

[http://www.justlinux.com/nhf/X_Window/Creating_Multiple_GDM_Logins_on_a_Single_Workstation.html](http://www.justlinux.com/nhf/X_Window/Creating_Multiple_GDM_Logins_on_a_Single_Workstation.html)

Thank you but I have actually found that my audio bug is caused by loading wine in the additional xserver. Nevertheless, I shall review the link.

---

