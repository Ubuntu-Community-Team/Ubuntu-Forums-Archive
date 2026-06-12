---
title: "Setting up a MiFi"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by sueken on 2010-12-03
i am running ubuntu maverick on a acer aspire netbook, how do I setup a Huawei E5830 MiFi.

---

### Post by cariboo on 2010-12-03
Plug it in, and see what happens. Check dmesg to see if it is detected and the driver loaded. Open an Applications->Accessories->Terminal and type:

```
dmesg | tail -n15
```

If you don't understand what you are seeing, paste the outpput in your next post.

---

