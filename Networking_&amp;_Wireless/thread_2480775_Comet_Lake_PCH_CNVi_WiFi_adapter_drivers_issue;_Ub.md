---
title: "Comet Lake PCH CNVi WiFi adapter drivers issue; Ubuntu 22.04"
date: 2022-11-09
forum: Networking &amp; Wireless
---

### Post by gopigof on 2022-11-09
Following an NVIDIA drivers update, my WiFi adapter drivers were gone and the WiFi icon disappeared from system tray and settings menu. Whenever the same issue occurred prior, I was able to resolve it by re-installing `linux-extras` package for my kernel version, but this time the issue isn't getting fixed. I tried most of solutions for similar issues found on the internet, but I feel I maybe making the situation worse. 

- I tried booting to old kernel version [5.15.0-50] to fix it from there, but the same problem persisted there too. WiFi wasn't available on system tray.
- I manually installed the `backport-iwlwifi-dkms` package as a fix. Prior to installing this package, the response to the command: "lshw -C network" showed the network as "UNCLAIMED", but after installing the package it is as in the wireless-info dump.
- My WiFi adapter drivers don't show up in Ubuntu Additional drivers list. I tried rebooting and running "apt-get update -y" already, but it didn't work


Does anyone have any idea on how to get WiFi running back on?

---

### Post by chili555 on 2022-11-10
Please run:

```
sudo apt purge backport-iwlwifi-dkms
```

Reboot and show us the result of:

```
sudo modprobe iwlwifi
sudo dmesg | grep iwl
```

---

