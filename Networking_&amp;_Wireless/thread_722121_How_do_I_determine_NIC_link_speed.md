---
title: "How do I determine NIC link speed?"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by GordonCopestake on 2008-03-12
How do I determine (over SSH) what speed my NIC is linking at (1Gb or 100Mb). Is there an easy way to tell?

Thanks in advance

---

### Post by dcstar on 2008-03-12
> **GordonCopestake said:**
> How do I determine (over SSH) what speed my NIC is linking at (1Gb or 100Mb). Is there an easy way to tell?

Thanks in advance

```
ethtool eth0
```

---

### Post by prshah on 2008-03-12
> **GordonCopestake said:**
> How do I determine (over SSH) what speed my NIC is linking at (1Gb or 100Mb). Is there an easy way to tell?

Thanks in advance

```
sudo mii-tool eth0
```

Cheers,
PRShah

---

