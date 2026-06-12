---
title: "Bash: How to wipe/ put zero bits on a partition of a CF flashdisk?"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-09
Hello,

I would like learn how to use bash for such operations. Mostly they say to use some special X11 apps. but without X11? is ti possible ?

regards

---

### Post by gzarkadas on 2010-10-11
Use:
```

dd bs=1M if=/dev/zero of=/dev/[your-target-partition]

```

---

