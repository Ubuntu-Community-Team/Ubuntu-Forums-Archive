---
title: "Alfa AWUS036H wifi adpter not working on ubuntu 15.10"
date: 2016-04-03
forum: Networking &amp; Wireless
---

### Post by Joseph_Adamo on 2016-04-03
Hello, I just installed ubuntu 15.10 and my wifi card is not working as it should and works perfectly fine with windows, It will connect to wifi, but will have very slow download speeds at first and then move to a grinding hault in which the internet is not even usable, it will however work with wired connections but due to the fact I instaled ubuntu on a laptop, it kinda defeats the purpose. The wifi card already in my laptop does not hold a stable connection wit ubuntu either, any help would be greatly appreciated.

---

### Post by Bucky Ball on 2016-04-03
*Thread moved to **Networking & Wireless**.*

Welcome. Please run the wirelessinfo link in my signature and post the output between code tags (see the link in my signature for how to do that also). Thanks.

Unplug the ethernet cable when you're running the script. In fact, unplug any external wireless device and let's see what you have in the box wireless-wise.

---

### Post by Joseph_Adamo on 2016-04-03
when I ran the wireless info as an executable file, it created a text file but there was nothing inside, i tried it multiple times and nothing happened :/ but if you want to know what I have out of the box, when i run sudo slhw  and scroll down to my internal wifi (no usb plugged in) this is the information 

description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 01
                serial: 24:ec:99:b5:06:95
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=4.2.0-34-generic firmware=N/A ip=192.168.43.62 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103ff

---

