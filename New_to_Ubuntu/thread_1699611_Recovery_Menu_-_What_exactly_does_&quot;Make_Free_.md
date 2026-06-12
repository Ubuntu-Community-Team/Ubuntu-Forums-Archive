---
title: "Recovery Menu - What exactly does &quot;Make Free Space&quot; do?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by emarkay on 2011-03-03
It may be obvious, but what procedures and functions does it do?

Also, can it be performed after boot, and if so with what command?

Thanks!

---

### Post by plucky on 2011-03-04
> **emarkay said:**
> It may be obvious, but what procedures and functions does it do?

Also, can it be performed after boot, and if so with what command?

Thanks!

```
sudo apt-get clean
``` Deletes all the .deb files in the /var/cache/apt/archives/ directory.

From ```
cat /usr/share/recovery-mode/options/clean
```

Good Luck

---

### Post by emarkay on 2011-03-04
So it's the "same thing" as "Clean - and related as "Autoclean".

Thanks!

---

