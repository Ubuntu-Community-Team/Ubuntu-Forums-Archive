---
title: "RTL8723BE PCIe Wireless Network Adapter - connection keeps dying"
date: 2015-12-26
forum: Networking &amp; Wireless
---

### Post by awjm on 2015-12-26
Sorry if this has been covered before; I did search! And I need extra help because I'm not much of a wizard at all.

So, below is my wireless adapter model. It is connects to WiFi fine and starts working. Then after some time the internet connection is no longer working although Ubuntu tells me I'm still connected to the WiFi. I've checked the internet connection on other devices and is working fine at the time, so it has to be an issue with Ubuntu only. Can anyone help me get rid of this nasty problem as it's the most annoying thing! Is there a quick fix? Is a driver missing? Am I right in saying that versions of ubuntu from several years ago never had this kind of issue and found drivers for hardware better?

description: Wireless interface
product: RTL8723BE PCIe Wireless Network Adapter
vendor: Realtek Semiconductor Co., Ltd.

---

### Post by Hadaka on 2015-12-27
Hi, see if this helps..
```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf 
sudo modprobe -rfv rtl8723be 
sudo modprobe -v rtl8723be
```
thanks.

---

### Post by slage63 on 2015-12-28
one more thanks

---

