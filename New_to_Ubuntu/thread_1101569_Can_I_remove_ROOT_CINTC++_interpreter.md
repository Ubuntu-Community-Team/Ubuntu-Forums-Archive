---
title: "Can I remove ROOT CINT/C++ interpreter?"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by davidstri on 2009-03-20
I downloaded a CINT/C++ interpreter called ROOT, but now I want to remove it, because it has some objectional pictures. I tried removing it with sudo apt-get remove ROOT, but it didn't work. How can I safely remove this?

---

### Post by cariboo on 2009-03-20
If you installed from source, and still have the source directory on your hard drive, simply go into the source directory and type:

```
sudo make uninstall
```

Jim

---

### Post by davidstri on 2009-03-20
I found a different way :). I found out where the objectional icons were located.The first two were in /usr/share/root/icons, but it told me I didn't have permission to delete them. So I used ```
sudo nautilus
``` to give me superuser privileges in nautilus. I deleted them, and then navigated to /usr/share/icons/hicolor/48X48/apps/ and deleted the desktop icon. But it had a back-up icon in /usr/share/pixmaps/ which I also deleted. Now I can keep ROOT without the objectional icons :).

---

