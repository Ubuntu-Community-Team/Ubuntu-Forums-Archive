---
title: "Windows borders are missing"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Tart on 2010-06-03
Hey All,

I did something stupid to my netbook. I was experimenting with compiz. I installed it, it didn't really work, I uninstalled it. But now my windows borders are missing. ```
metacity --replace
``` helps but only for current session (if I close terminal - problem is back), if I log off/restart problem is back. Is there a way to permanently fix the problem?

Thanks!

---

### Post by Legendary_Bibo on 2010-06-03
> **Tart said:**
> Hey All,

I did something stupid to my netbook. I was experimenting with compiz. I installed it, it didn't really work, I uninstalled it. But now my windows borders are missing. ```
metacity --replace
``` helps but only for current session, if I log off/restart problem is back. Is there a way to permanently fix the problem?

Thanks!

```
compiz --replace
```

And download the Compiz fusion icon from the software center.

---

### Post by Tart on 2010-06-03
Thank you!
I installed Compiz fusion icon. did compiz --replace. It gave me bunch of error messages. But after that I was able to go back to appearance and change "No Effects" before it was grayed out. Now things back to normal. 

Thanks

---

### Post by qwertyuiopasdfghjklzxcvbn on 2010-06-03
Go to compiz config and change the setting in widnow decoration to

command: metacity --replace

---

