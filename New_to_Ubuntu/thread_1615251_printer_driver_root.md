---
title: "printer driver root"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by nbusiness on 2010-11-06
I'm  installing a printer driver and it is asking for the root password i'm useing ubuntu 10.04 lts printer x7675 lexmark.

---

### Post by Hippytaff on 2010-11-06
use the password you used when you installed ubuntu

---

### Post by nbusiness on 2010-11-06
I have tried that also it tell me it's incorrect but I use it that password when I log on so I know it's works.

---

### Post by Hippytaff on 2010-11-06
maybe
```

passwd

```
to change the password, are you the only user, if not are you in the sudoers file?

---

### Post by spcwingo on 2010-11-06
To become root in Ubuntu use sudo.  So instead of using su or su root try this:

```
sudo -i
```

---

### Post by nbusiness on 2010-11-07
THanks for all help I'm able to move forward thanks.

---

