---
title: "Conky Won't Read Data from RealTek 8188EUS"
date: 2022-05-01
forum: Networking &amp; Wireless
---

### Post by wmichaelb2 on 2022-05-01
I'm using Xubuntu on an old Dell Latitude E6410. I had weak reception with the internal Broadcom chip, and so I installed the Broadcom proprietary driver via the Driver Manager app. Immediately, my Conky display quit importing info from the system. I learned per [https://askubuntu.com/questions/350409/conky-does-not-display-wireless-info](https://askubuntu.com/questions/350409/conky-does-not-display-wireless-info) that that driver blocks Conky access; one needs to have Conky with root access. The suggestion was to run

```
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/conky
```

which I did, but it made no difference. Taking a different tack, I installed a TP-Link TL-WN725NV1, which uses the RealTek 8188EUS chip, and installed the driver for that chip. The adapter works fine, good speed and good sensitivity. Still no Conky joy. Does anyone have any other suggestions on what to try? Thanks in advance.

---

