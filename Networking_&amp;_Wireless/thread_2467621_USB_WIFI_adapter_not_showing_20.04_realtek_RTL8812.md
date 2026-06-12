---
title: "USB WIFI adapter not showing 20.04 realtek RTL8812AU"
date: 2021-10-02
forum: Networking &amp; Wireless
---

### Post by nolive721 on 2021-10-02
Hello

I am completely struggling to get my USB wireless adapter to show in Ubuntu 20.04

I tried to follow this tutorial but it still doesnt work [https://askubuntu.com/questions/1185952/need-rtl8814au-driver-for-kernel-5-3-on-ubuntu-19-10](https://askubuntu.com/questions/1185952/need-rtl8814au-driver-for-kernel-5-3-on-ubuntu-19-10)

Any help appreciated

thanks a lot

---

### Post by QIII on 2021-10-02
Moved to Networking & Wireless.

---

### Post by morrownr on 2021-10-04
> **nolive721 said:**
> Hello

I am completely struggling to get my USB wireless adapter to show in Ubuntu 20.04



Take a look at this site:

[https://github.com/morrownr?tab=repositories](https://github.com/morrownr?tab=repositories)

Each repo, including the one for the 8812au chipset, includes a lot of information to include installation instructions.

I've seen a lot of confusion over the years regarding whether an adapter has a 8812au or 8811au chipset so if you want to post the results of the following, we could double check:

```
lsusb
```

---

