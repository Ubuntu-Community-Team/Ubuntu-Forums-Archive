---
title: "Slow wifi when using Ubuntu 17.04, but faster in Windows 10"
date: 2017-06-18
forum: Networking &amp; Wireless
---

### Post by aks2161989 on 2017-06-18
Hi,

I am a newcomer to Ubuntu. I have a dual-boot system with Ubuntu 17.04 Zesty Zapus and Windows 10. When I boot Ubuntu, the wifi is much slower and it **disconnects when I move to another room** (away from the broadband router). However, when I am using windows, it remains connected to wifi even when I move to another room.

I tried the following command:
```
lspci | grep Wireless
```

It shows the following output:
```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
```

Is there a working solution to this problem? Forgive me if this question has been asked before, kindly send me a link to the answer.

---

### Post by praseodym on 2017-06-18
Hi,

please try:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot. If its not working better try it again with **ant_sel=2**

---

### Post by aks2161989 on 2017-06-19
> **praseodym said:**
> Hi,

please try:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot. If its not working better try it again with **ant_sel=2**

Hi praseodym,

Thank you so much! I tried the command exactly as it is. Now I am able to connect to wifi even from another room. It worked well with [B]ant_sel=1.

[/B]Thank you again!

---

