---
title: "Icons on the desktop"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by squrl on 2010-09-28
I am searching for a way to place files and folders on the desktop without an icon. 

The last attempt was to create an icon small and transparent then save it. Then go to properties and replace the original icon with it. This works but only for that session. After the machine is booted again the icon is back. 

Can anybody tell me how to make this a permanent change or at least how to get rid of desktop icons.

Thanks

---

### Post by jtarin on 2010-09-28
Which icons?

---

### Post by Paqman on 2010-09-28
> **squrl said:**
> 
Can anybody tell me how to make this a permanent change or at least how to get rid of desktop icons.


Hit Alt-F2 and enter:
```
gconf-editor
```

Go to Apps > Nautilus > Desktop in the menu on the left. Uncheck the boxes for anything you want to not show up.

---

### Post by kryg3r on 2010-09-28
i tried it and it works. thank you

---

