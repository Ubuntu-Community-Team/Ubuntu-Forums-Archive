---
title: "wifi drivers are not working on ubuntu 23.10"
date: 2023-12-24
forum: Networking &amp; Wireless
---

### Post by nixobe on 2023-12-24
i tried to use live ubuntu 23.10 on macbook pro late 2013 retina i7, but the drivers i applied for ubuntu are not working (wifi doesn't work)
the wifi adapter is: BCM4360 802.11ac Wireless Network Adapter
• Using dkms source for the Broadcom STA Wireless driver from broadcom-sta-dkms (proprietary)

---

### Post by chili555 on 2023-12-24
After you installed the driver, did you load it?

```
sudo modprobe wl
```

Are there any clues in the message log?

```
sudo dmesg | grep wl
```

---

