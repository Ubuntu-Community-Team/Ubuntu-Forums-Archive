---
title: "Prebuilt driver for Realtek 8821CE"
date: 2021-03-30
forum: Networking &amp; Wireless
---

### Post by lazloman on 2021-03-30
My ASUS laptop only has wireless, and I don't have a USB WiFi dongle, so I can't connect it to the network. Is there a prebuilt driver I can use with my laptop? Its a 14" ASUS Celeron.
Thanks

---

### Post by CelticWarrior on 2021-03-30
The best and easiest way to install the driver is to have an alternative internet connection. Ethernet when available or USB tethering from any Android or iOS phone are obvious choices. Then it's just a matter of installing the driver already available at Ubuntu repositories:

```
sudo apt install 8821ce-dkms
```

Alternative you can download the package using other computer: [https://packages.ubuntu.com/focal/rtl8821ce-dkms](https://packages.ubuntu.com/focal/rtl8821ce-dkms)

---

### Post by mikewhatever on 2021-03-30
No. Drivers are usually built against a specific kernel version, as opposed to your idea of a driver built once and used everywhere.

There is no easy solution to your problem: there is only wireless, and to use it you need a driver, which is impossible to get without wireless. Might need to invest into an Ethernet-to-USB device, or use an phone as one.

---

### Post by praseodym on 2021-03-31
USB Tethering with your smartphone?

---

