---
title: "Is Swap partition in use?"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by IanAdams on 2010-09-27
Is there a way to determine if the swap partition is being used by the operating system?

---

### Post by amauk on 2010-09-27
```
swapon -s
```

---

### Post by NightwishFan on 2010-09-27
Even look in System -> Administration -> System Monitor if you want. Go to the resources tab, and if it says (for example) 0 Bytes Of 3.9 Gib, it is in use. Swap is not always needed, if you have enough ram it will always be empty. Keep the swap though, it comes in handy in a pinch. (Load a large image in gimp).

---

### Post by IanAdams on 2010-09-27
Thank you both.  Exactly what I needed.

---

