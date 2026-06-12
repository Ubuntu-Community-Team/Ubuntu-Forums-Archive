---
title: "Sky Lake and Atheros QCA6174"
date: 2016-06-27
forum: Networking &amp; Wireless
---

### Post by fjgaude on 2016-06-27
Using Z170 Intel chip set, Ubuntu 16.04, but no WiFi. The Qualcom QCA6174 is not working, no driver.

Has anyone found a solution to this issue?

Thanks!

---

### Post by jeremy31 on 2016-06-27
The driver should be fine in 16.04 but the firmware is missing
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```
Reboot

---

### Post by fjgaude on 2016-06-27
Thanks, will install it and report back.

---

### Post by fjgaude on 2016-06-27
Ok, Jeremy, that did the trick. It works, thanks again.

---

