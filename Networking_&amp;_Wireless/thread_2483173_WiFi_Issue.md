---
title: "WiFi Issue"
date: 2023-01-22
forum: Networking &amp; Wireless
---

### Post by itsentdev on 2023-01-22
After I managed to install ubuntu, my Realtek 8811CU WiFi dongle isn't recognized, nor do I have a page for WiFi in Settings.
How do I fix this?

---

### Post by jeremy31 on 2023-01-22
Check in terminal ```
mokutil --sb
```
As Secure Boot can not be enabled for this to work
```
sudo apt update
sudo apt install dkms git
git clone https://github.com/morrownr/8821cu-20210118.git
cd 8821cu-20210118
sudo ./install-driver.sh
```
Reboot

---

### Post by itsentdev on 2023-01-22
I, uh, don't have any wifi. That includes internet. I don't have a wired connection, if I had one there wouldn't be much of an issue.

---

### Post by jeremy31 on 2023-01-22
Can you USB tether to a smart phone?  What kernel version? ```
uname -r
```

---

### Post by itsentdev on 2023-01-23
I managed to USB connect to my phone and install the driver, WiFi works fine now. Why doesn't the driver come with the third-party drivers for WiFi and graphics hardware?

---

