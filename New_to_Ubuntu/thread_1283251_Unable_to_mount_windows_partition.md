---
title: "Unable to mount windows partition"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by Falc7 on 2009-10-05
I get this error message: 
[http://img74.imageshack.us/img74/571/snapshot1d.png](http://img74.imageshack.us/img74/571/snapshot1d.png)

---

### Post by Dangger on 2009-10-05
> **Falc7 said:**
> I get this error message: 
[http://img74.imageshack.us/img74/571/snapshot1d.png](http://img74.imageshack.us/img74/571/snapshot1d.png)

You are getting this error because the partition apparently belongs to another user (uid=1000). 

Type the command "id" without quotes in the terminal to know your uid number and see if it's different than uid=1000.

---

### Post by Falc7 on 2009-10-05
Here is the result
```
uid=1000(jamie) gid=1000(jamie) groups=4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),122(sambashare),1000(jamie)

```

I've got kubuntu installed along side ubuntu, i've noticed i can view the windows partition from ubuntu, but not from kubuntu.

---

