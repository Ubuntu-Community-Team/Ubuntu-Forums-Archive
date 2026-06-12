---
title: "WIFI not working on Acer Aspira E5-552G without D-Link USB adapter"
date: 2016-10-16
forum: Networking &amp; Wireless
---

### Post by neva108 on 2016-10-16
Hello,
I have installed Ubuntu 14.04 on my new Acer Aspire E5-552G. Wireless connection is working only with D-Link wireless USB adapter, is it possible to work without adapter?

 Network controller [0280]: Qualcomm Atheros Device [168c:0042]

 Here is a output:

---

### Post by howefield on 2016-10-16
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by jeremy31 on 2016-10-16
This should work ```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.4_all.deb
sudo dpkg -i linux-firmware_1.157.4_all.deb
```

Reboot

---

### Post by neva108 on 2016-10-17
Dear howefield,
Thank you for moving thread in another forum. The problem was solved very quick.
Kind regards

---

### Post by neva108 on 2016-10-17
Dear Jeremy,
THANKS A LOT. Your suggestion solved the problem.
Best regards

---

