---
title: "screen tearing with media"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by insanity99 on 2009-06-29
when i watch videos their is screen tearing, anyway to fix this?

---

### Post by Thingymebob on 2009-06-29
I believe its an issue with the ATI driver while using compiz, disable compiz when you're watching videos, install fusion-icon for a convenient way of doing this.

---

### Post by insanity99 on 2009-06-29
i have fusion-icon, how do i disable it with it?

---

### Post by NightwishFan on 2009-06-29
If that does not work, press alt+f2 and type this command:
```
gstreamer-properties
```

Try either enabling or disabling xvideo. However I think Compiz is the issue.

---

