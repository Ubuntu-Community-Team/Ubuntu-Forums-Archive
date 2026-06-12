---
title: "No Wi-Fi Adapter Found"
date: 2019-12-23
forum: Networking &amp; Wireless
---

### Post by whatiswrong on 2019-12-23
Wi-Fi is not working on my Asus Zenbook, tried everything that I could find but nothing worked.

Wireless script:
[https://pastebin.com/aKiN3Zsd](https://pastebin.com/aKiN3Zsd)

Thanks in advance

---

### Post by praseodym on 2019-12-23
There it is:

```
00:14.3 Network controller [0280]: Intel Corporation Device [8086:02f0]
    Subsystem: Intel Corporation Device [8086:0074]
```

Please run
```

sudo modprobe -v iwlwifi
dmesg | grep iwl
```

---

### Post by jeremy31 on 2019-12-23
```
sudo add-apt-repository ppa:canonical-hwe-team/backport-iwlwifi
sudo apt-get update
sudo apt install backport-iwlwifi-dkms
```
Reboot

---

