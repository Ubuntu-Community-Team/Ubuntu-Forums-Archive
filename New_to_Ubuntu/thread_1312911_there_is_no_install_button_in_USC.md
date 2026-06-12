---
title: "there is no install button in USC"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by U-boy on 2009-11-03
I've just installed Ubuntu 9.10 and trying to install some application through Ubuntu Software Center. But there is no install button under application. Only remove button under those that are already installed. 

Can someone help me please?

---

### Post by danastasio on 2009-11-03
what program is it, its likely you do already have it installed.

---

### Post by U-boy on 2009-11-03
I couldn't install any program. But now after I just reinstalled Software Center itself it's ok.

---

### Post by slmat27 on 2010-02-03
> **U-boy said:**
> I couldn't install any program. But now after I just reinstalled Software Center itself it's ok.
I have the same problem you had, so how did you manage to overcome it by re-installing Ubuntu Software Center. I don't know how to re-install it.

Thanks in advance...

---

### Post by nhasian on 2010-02-03
you probably just need to open a terminal from Applications->Accessories and enter the following command:

```
sudo apt-get update && sudo apt-get upgrade
```

---

