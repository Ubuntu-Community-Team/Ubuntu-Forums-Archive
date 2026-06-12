---
title: "Fan never comes on"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by LinnetLegs on 2009-01-17
When I was using vista, my fan came on pretty regularly. Since I have been using ubuntu, my fan has never come on. The computer does not feel hot.

Is there a problem with the fan?

---

### Post by niteshifter on 2009-01-17
> **LinnetLegs said:**
> When I was using vista, my fan came on pretty regularly. Since I have been using ubuntu, my fan has never come on. The computer does not feel hot.

Is there a problem with the fan?

Probably not. I've never used Vista, but noticed the same when I dual-booted with XP: Windows ran the fan more than Ubuntu did.

You can check what the temperature of the CPU is by opening a terminal (Applications > Accessories > Terminal) and typing this:
```
cat /proc/acpi/thermal_zone/THM/temperature
```

---

### Post by LinnetLegs on 2009-01-17
Thanks

---

