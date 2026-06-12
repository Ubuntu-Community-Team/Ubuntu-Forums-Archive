---
title: "Finding the MAC address"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by SteelCore on 2009-01-31
Hi,
What is the shell command to find out your MAC address?
Thanks

---

### Post by TCSnyder on 2009-01-31
it's 

```
ifconfig
```

---

### Post by taurus on 2009-01-31
I believe ifconfig would do.

```
/sbin/ifconfig
```

---

### Post by prshah on 2009-01-31
> **SteelCore said:**
> Hi,
What the shell command to find out your MAC address?


ifconfig, as suggested will give you the MAC address, marked as HWaddr. You can also use```
ifconfig | grep -i hwadd
``` to strip out unnecessary information.

---

### Post by SteelCore on 2009-01-31
> **prshah said:**
> ```
ifconfig | grep -i hwadd
```

That's neat.

Thanks to all.

---

