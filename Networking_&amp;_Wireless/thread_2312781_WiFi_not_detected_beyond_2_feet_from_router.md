---
title: "WiFi not detected beyond 2 feet from router"
date: 2016-02-07
forum: Networking &amp; Wireless
---

### Post by nikhil20 on 2016-02-07
Hello , I am new to Ubuntu.I have dual dual booted with Windows 10 in laptop. While using Ubuntu, it is detecting and connecting to WiFi router(DLink DIR-600M) when it is only 2 feet from it, on moving more than 2 feet away,it is not able to detect any WiFi and is getting disconnected.But when using Windows, WiFi is working till 20 feet.

---

### Post by jeremy31 on 2016-02-07
Post result from terminal for ```
lspci -nnk | grep -iA2 net
```

Is this a HP laptop?

---

### Post by nikhil20 on 2016-02-08
> **jeremy31 said:**
> Post result from terminal for ```
lspci -nnk | grep -iA2 net
```

Is this a HP laptop?

Yes its a HP Laptop . Result of code is:
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: SANJI
	Subsystem: Hewlett-Packard Company Device [103c:804c]
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:80cc]
	Kernel driver in use: r8169

---

### Post by jeremy31 on 2016-02-08
[http://askubuntu.com/a/722904/300665](http://askubuntu.com/a/722904/300665)

If you get an error about package not installed during the first command, just move to the next.

If you have any other errors, post them

---

### Post by nikhil20 on 2016-02-11
Error-
bash: cd: rtlwifi-new: No such file or directory

---

### Post by jeremy31 on 2016-02-11
That was a typo ```
cd rtlwifi_new
```

---

### Post by nikhil20 on 2016-02-12
Thanks a lot dude! I am now able to connect to WiFi from a long distance.:D

---

