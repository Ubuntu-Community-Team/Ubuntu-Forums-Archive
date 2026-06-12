---
title: "Realtek RTL8723AE / Toshiba Satellite C850"
date: 2013-10-17
forum: Networking &amp; Wireless
---

### Post by Jake Sweeney on 2013-10-17
Hello everyone!

I'm having troubles with my wireless networking in Ubuntu 13.04. The problem is that it can't seem to establish a secure connection with my router - It will stay connected for a few minutes, then disconnect, then reconnect again etcetera. My computer is a Toshiba Satellite C850 with a Realtek RTL8723AE wireless adapter.

I know that it isn't an issue with range or anything as my Windows 7 partition seems to connect to the network just fine.

Any suggestions will be very helpful :p

---

### Post by Hadaka on 2013-10-17
Hi Jake, please post the output of..
```
lspci -nnk | grep -iA3 net
```
thanks.

---

### Post by Jake Sweeney on 2013-10-17
Here is the output to  lspci -nnk | grep -iA3 net:

```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0724]
	Kernel driver in use: rtl8723ae
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fb37]
	Kernel driver in use: r8169



```

---

### Post by Hadaka on 2013-10-17
Hi, give this a try..
please do..
```
sudo modprobe -r rtl8723ae
sudo modprobe rtl8723ae swenc=1
```
this will last untill the first boot. If it helps
to make permanent then do..
```
sudo gedit /etc/modprobe.d/rtl8723ae.conf
```
add this one line of code.
```
options rtl8723ae swenc=1
```
save and close gedit.

---

### Post by Jake Sweeney on 2013-10-18
I've done the commands and It's seemed to work; the connection can stay established for a prolonged period of time. Now the network will have peaks of fast connection time and then peaks of a really slow connection - the connection will take about 5 minutes to load a web page. 

I have no idea what to do! :/

---

