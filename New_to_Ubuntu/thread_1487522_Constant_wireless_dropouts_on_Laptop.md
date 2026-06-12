---
title: "Constant wireless dropouts on Laptop"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by deancasino on 2010-05-19
I'm getting constant wireless dropouts on my Acer Travelmate 2480. I'm running 10.04 on it and have tried install madwifi which advised no supported hardware detected.

Any ideas?

---

### Post by deancasino on 2010-05-19
I take it I'm screwed. Wonderful.

---

### Post by iponeverything on 2010-05-19
> **deancasino said:**
> I take it I'm screwed. Wonderful.

I would not say that quite yet.

What does lspci and lshw -c network identify you wireless hardware as?

---

### Post by zkriesse on 2010-05-19
What is your wireless card specs?

---

### Post by deancasino on 2010-05-23
Alright, I hope someone can let me know what drivers to install to stop the drop outs now, thank you in advance for any help you guys can give.

lspci: 0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

lshw -c network: 
*-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wlan0
       version: 01
       serial: 00:19:7d:42:af:f1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=10.1.1.4 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg

---

### Post by Ladkipz on 2010-05-25
I came accross this thread randomly through google search, however my TravelMate 2418AWLCi has the exact same problem. As I type this message my internet is dropping in and out. I never had a similar problems whilst using XP and it does get really annoying.

---

### Post by v1ad on 2010-05-25
use ndiswrapper it should fix it.

---

