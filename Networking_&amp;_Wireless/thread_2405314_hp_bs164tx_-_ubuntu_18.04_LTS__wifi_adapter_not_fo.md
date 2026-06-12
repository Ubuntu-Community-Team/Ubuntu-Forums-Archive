---
title: "hp bs164tx - ubuntu 18.04 LTS : wifi adapter not found"
date: 2018-11-04
forum: Networking &amp; Wireless
---

### Post by mrfinch2 on 2018-11-04
Hi, I just purchased this laptop and installed Ubuntu. But the wifi not working.

In the settings on the wifi Page, it says

*Wifi adaptor not found*.

Please help me.

---

### Post by jeremy31 on 2018-11-04
Post results from terminal for ```
lspci -nnk | grep -iA3 net
```

---

### Post by mrfinch2 on 2018-11-08
> **jeremy31 said:**
> Post results from terminal for ```
lspci -nnk | grep -iA3 net
```

lspci -nnk | grep -iA3 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8329]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]

---

### Post by jeremy31 on 2018-11-08
Do
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

Check ```
mokutil --sb-state
```
If the result says the Secure Boot is enabled, reboot and go into BIOS settings and disable it and it should work

---

