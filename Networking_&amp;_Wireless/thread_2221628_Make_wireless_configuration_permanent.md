---
title: "Make wireless configuration permanent"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by andyhelloween on 2014-05-03
Hi all,

After a kernel upgrade, my Broadcom wireless BCM4313 was not working. After some investigation and issue some commands, I fixed it with: 

```
sudo modprobe -r hp-wmi
```

I couldn't find the right way to make it permanent. Tried to blacklist hp-wmi given *man modprobe says* *"-r"* stands for *"remove"*, but no joy.

Can anyone help me?

Cheers,
Andy.

---

### Post by chili555 on 2014-05-03
> Tried to blacklist hp-wmiHow exactly did you do that? May we see:```
cat /etc/modprobe.d/blacklist.conf
```Thanks.

---

