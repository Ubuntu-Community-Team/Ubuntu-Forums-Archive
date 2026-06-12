---
title: "Wireless connections are gone"
date: 2023-02-22
forum: Networking &amp; Wireless
---

### Post by tfors2005 on 2023-02-22
I've been using Ubuntu 22.04.1LTS 64bit on an early 2010s MacBook Air for a year and a half now. Yesterday, after a routine restart, I noticed that the device:
1. Didn't connect to a wifi network
2. Did not display the wifi icon/setting shortcut in the toolbar
3. Does not display connection options other than VPN under the network tab in settings

I attempted to remedy this by doing what other posts had suggested. I searched for network manager via terminal and was met with a "does not exsist" error. I then searched for the WPA and Network Services unit files and found that they were both enabled. Finally, I searched for my network card, a Broadcom BCM43224. It's there and I think functioning, but it keeps giving me a "network UNCLAIMED" message when I run "sudo lshw -C network." Finally, I attempted to uninstall and re-install the drivers for the card, this did not seem to do anything.

**additional note: this device does not have an ethernet port and I do not have an ethernet adapter for the Light Peak port

---

### Post by chili555 on 2023-02-22
Please run and post:

```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```

---

### Post by tfors2005 on 2023-02-22
> **chili555 said:**
> Please run and post:

```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```

Response is "Status: install ok installed"

---

### Post by chili555 on 2023-02-22
How about:```
sudo dpkg -s bcmwl-kernel-source | grep Status
lspci -nnk | grep 0280 -A3
```

---

