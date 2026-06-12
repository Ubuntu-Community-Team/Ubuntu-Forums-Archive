---
title: "Ubuntu PCs dropping wifi, other devices on wifi work OK"
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by hans12345 on 2015-11-30
I have a TP-Link router TL-WR841N (Atheros) with ethernet connections (that always work) and wifi working on both 2.4 Ghz and 5 GHz frequencies..

I have 4 devices that use wifi. The Internet radio and the Chromebook work perfectly, but the two Ubuntu PCs lose their wifi frequently. A disable/enable wifi starts the wifi again.

The Ubuntu PCs (a Lenovo C260 All-in-one running Xubuntu, and a home-built desktop with Ubuntu and a Belkin N300 USB wifi) are fully up to date. They have different wifi chips/setups.

The Belkin N300 had worked properly with my TP-Link router when mounted on a different PC (also running Ubuntu) earlier.

On the Lenovo (where I work now) lspci shows:
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)

Where should I be looking for a solution? Do I focus on the router or the Ubuntu PCs? 

If Ubuntu, 
- could it be a Ubuntu driver problem on 2 different wifi setups?
- could the Ubuntu PCs be affecting each other?

If router,
- Why do the radio and the Chromebook work ?
- Can it be due to the router working strangely on the 2 different radio frequencies?
- Can it be due to interference on one of the 2 different radio frequencies?

What info can I post to help track down the problem?

Thanks for your help.

---

### Post by hans12345 on 2015-12-01
The situation develops.

2 things:
- I changed the Belkin 300 N wifi dongle (802.11 n) for an old 802.11 ag one (the 50 kbps speed), and it works fine
- I tried an old laptop, also with a 802.11 ag wifi, and it works fine

So either I have a 802.11 n (the 300 kbps speed) problem related perhaps to the router, 
or
I have Ubuntu driver problems. I say this because I see the RTL8188EE Wireless Network Adapter (on the Lenovo) does have some older posts mentioning problems.

Any ideas?

How should I progress from here?

---

### Post by hans12345 on 2015-12-03
Strange developments.

Having changed the wifi dongle (802.11 n) USB on my homebuilt desktop to an older 802.11 ag (the 50 kbps speed)  USB, the Lenovo, with the RTL8188EE Wireless Network Adapter, works much better !

Wifi was dropping often, say every 5 minutes, now it runs for an hour or more.

---

