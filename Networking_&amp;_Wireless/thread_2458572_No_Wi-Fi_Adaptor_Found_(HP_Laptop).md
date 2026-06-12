---
title: "No Wi-Fi Adaptor Found (HP Laptop)"
date: 2021-02-27
forum: Networking &amp; Wireless
---

### Post by rebellious.ben on 2021-02-27
When I first bought the CPU about 2 years ago, I installed Ubuntu 18.00. I had the same issue, no wifi adaptor found.  The cpu has a Realtek RTL8821CE 802.11ac PCIe wireless network adaptor. So I did some research and I was able to download & install to Ubuntu what I needed to make the wifi work.  However a couple of months ago I downloaded an update to Ubuntu 18.04.5 LTS & now I am having the same issues but when I try to follow the steps to install to get my wifi back my computer already has everything but still won't find the wifi adaptor.  If anyone can help me it would be much appreciated.

---

### Post by praseodym on 2021-02-28
Try
```

sudo apt install rtl8821ce-dkms
```
Reboot and deactivate SecureBoot, if applicable

---

