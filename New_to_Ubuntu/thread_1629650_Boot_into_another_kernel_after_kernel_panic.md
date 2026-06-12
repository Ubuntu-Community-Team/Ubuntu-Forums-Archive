---
title: "Boot into another kernel after kernel panic"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by sajnanazeer on 2010-11-24
Hi,

Is there any way to make grub2 to boot to another kernel after a kernel panic ?

---

### Post by marshmallow1304 on 2010-11-24
Hold down shift to get the grub menu to appear then choose another kernel.  This of course assumes there are other kernels installed.

---

### Post by sajnanazeer on 2010-11-24
Can we automate this?

I want a solution that automatically boots to another kernel on restart after kernel panic.

---

### Post by bananas4370 on 2010-11-24
> **sajnanazeer said:**
> Can we automate this?

I want a solution that automatically boots to another kernel on restart after kernel panic.

You can get the system to automatically reboot after a delay by adding to /etc/sysctl.conf
```

kernel.panic = 10
```

Change the number to the number of seconds you want. Reload the settings by issuing

```
sudo sysctl -p
```

in a terminal.

I don't know how to get the system to reload a different kernel.

Cheers
Patrick

---

### Post by sajnanazeer on 2010-11-24
Thank you Patrick.

---

### Post by sajnanazeer on 2010-11-24
I am looking for any way to boot into another kernel without user intervention.

---

