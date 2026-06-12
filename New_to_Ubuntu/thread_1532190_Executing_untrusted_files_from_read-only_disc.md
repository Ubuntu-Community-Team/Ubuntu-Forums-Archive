---
title: "Executing untrusted files from read-only disc"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by new__buntu on 2010-07-16
I'm trying to install starcraft via wine, and as a result I need to give the install file executable permissions. I'd rather not have to copy the install file over to my computer and then use that. Is there a way to run the untrusted file (I can't change the permission on the disc because it's read-only)?

---

### Post by sisco311 on 2010-07-18
> **new__buntu said:**
> I'm trying to install starcraft via wine, and as a result I need to give the install file executable permissions. I'd rather not have to copy the install file over to my computer and then use that. Is there a way to run the untrusted file (I can't change the permission on the disc because it's read-only)?

Right click on the executable -> Open With -> Other Application -> Custom command:
```
wine
```

---

### Post by new__buntu on 2010-07-18
> **sisco311 said:**
> Right click on the executable -> Open With -> Other Application -> Custom command:
```
wine
```

Huh, it gives me the whole "this is not trusted software, cannot be executed" pop-up when I use "Wine Windows Program Loader". Then I decide to use "winebrowser" (which shows up three times in my applications list, oddly enough) and it opens without a problem. I don't suppose you could enlighten me as to why that is.

---

