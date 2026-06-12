---
title: "installing Wireless  USB driver in Ubuntu 22.04"
date: 2022-05-05
forum: Networking &amp; Wireless
---

### Post by rkpdl on 2022-05-05
How can I Install wireless driver for this modeled usb?
 ID 0bda:f179 Realtek Semiconductor Corp. RTL8188FTV 802.11b/g/n 1T1R 2.4G WLAN Adapter


please help

---

### Post by jeremy31 on 2022-05-05
Check ```
mokutil --sb-state
```
As Secure Boot needs to be disabled in UEFI/BIOS settings, then
```
sudo add-apt-repository ppa:kelebek333/kablosuz
sudo apt-get update
sudo apt-get install rtl8188fu-dkms
```
Reboot

---

### Post by rkpdl on 2022-05-05
Thanks! worked for me.

---

