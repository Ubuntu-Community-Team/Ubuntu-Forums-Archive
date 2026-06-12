---
title: "Getting wireless on Gusty"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by erik_gil on 2007-12-03
Hello, I was wondering if someone could help me get my wireless up and running, I'm running a fresh install of gusty(the 64 one). My laptop is a, Toshiba Satellite A215-S4757 and from what I know right now is that my im using an,  Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter. Please help this Linux newbie. Thanks.

---

### Post by daengbo on 2007-12-03
Is your driver recognized in System -> Administration -> Restricted Drivers?

---

### Post by erik_gil on 2007-12-03
Yes it is, I see "Atheros Hardware Acess Layer(HAL)

---

### Post by daengbo on 2007-12-03
Is that driver checkd to turn it on? After you do that, you should be able to go to the network manager (it's in the upper right corner of your screen) and choose your network.

---

### Post by erik_gil on 2007-12-03
Yes it is turned on, Its always been on. I think there might be something wrong with my network manager. It only shows, Wired and Modem connection, nothing for wireless.

Just thought of this, maybe it will help out. My router is a , Netgear WGT624 v3 and im using a WPA-PSK[TKIP] Security Encryption its on Channel 11, and g and b mode.

---

### Post by speedwell68 on 2007-12-03
Is the routers SSID hidden or broadcasted.  I have found when using WPA-PSK on my Netgear router that the Network Manager applet will only see my wireless connection if the SSID is set to broadcast.  It should see it as soon as you type in the SSID name and pre shared key, but it doesn't.  It'll work under WEP if the SSID is hidden but not under WPA.

---

### Post by erik_gil on 2007-12-03
Yeah its set to broadcast, but network manager isnt picking it up.

---

### Post by rustybronco on 2007-12-03
See my signature about WPA Connection - WPA-PSK or WPA2-PSK

---

