---
title: "Help in setting up Centrino Wireless-N 1000"
date: 2016-09-20
forum: Networking &amp; Wireless
---

### Post by ribaaa on 2016-09-20
Hi,

I am new to Linux and I would kindly ask for support in setting up my WiFi connection.
Printout from wifi script is in attachment.

Thanks a lot

---

### Post by wildmanne39 on 2016-09-20
Please do:
```
echo "blacklist dell-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot does the wifi come on?

---

### Post by ribaaa on 2016-09-21
Unfortunately problem is still present

---

### Post by wildmanne39 on 2016-09-21
What kind of laptop is it? please post a new file from the wireless script.
Thanks

---

### Post by ribaaa on 2016-09-21
After another restart wifi connection was ok.
Thanks a lot for fast support.

---

