---
title: "Wi-Fi drivers not available for Ubuntu-16.04 LTS for HP 15-bs576tx Notebook"
date: 2017-11-21
forum: Networking &amp; Wireless
---

### Post by kaushal-p on 2017-11-21
I have purchased HP laptop(model number 15-bs576tx) Notebook having DOS as an operation system.
I installed Ubuntu-16.04 LTS Operating System but wifi is not working in that.
I tried with Ubuntu-14.04 LTS OS also.But was unable to find Ubuntu wifi drivers(.deb) file.

Please help me in solving this issue.

Note: Not a hardware issue as in windows wifi works.


Thanks in advance.

---

### Post by jeremy31 on 2017-11-21
Open terminal and enter ```
lspci -nnk | grep -iA3 net
```
Post the results

---

### Post by aniket.kudale on 2018-05-01
```
Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	DeviceName: Hanksville Gbe Lan Connection
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:832a]
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
	DeviceName: WLAN
	Subsystem: Hewlett-Packard Company Device [103c:8319]
```

---

### Post by chili555 on 2018-05-01
> Realtek Semiconductor Co., Ltd. Device [10ec:[COLOR="#FF0000"]d723[/COLOR]]Please see: [https://askubuntu.com/questions/983251/realtek-semiconductor-rtl8723de-device-d723-issue](https://askubuntu.com/questions/983251/realtek-semiconductor-rtl8723de-device-d723-issue)

---

