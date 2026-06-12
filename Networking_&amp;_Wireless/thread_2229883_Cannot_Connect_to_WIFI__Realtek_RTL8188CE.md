---
title: "Cannot Connect to WIFI:  Realtek RTL8188CE"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by GnowledgedGnome on 2014-06-15
***I AM RUNNING UBUNTU 14.04 FROM A FLASH DRIVE***
I previously tried to install ubuntu, but could not resolve an issue with my wireless (my wireless sofware switch was not supported)

On Toshiba Satellite L630-Bt2N15 and am unable to connect to my home wifi, **while running from the USB**. I can select a network from a list of wifi connections and it attempts to connect, but eventually tells me it is unable to connect. My router isn't having any issues as far as I can tell. Booting with windows I am not having issues and my phone connects fine. Ethernet connection works just fine. 

Looking around the forums I was unable to find a solution to my issue. 


One thread asked a user to run this code: ```
lspci -nnk | grep -iA2 net
```

The results:
 ```
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: atl1c
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
```

A[ sticky post ]("http://ubuntuforums.org/showthread.php?t=370108")asked for the attached output. The same post lead me to [a page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI") that let me know my wireless hardware IS compatible
************EDIT:  After completing a clean install of Ubuntu I was able to get wireless to work. I used the instructions from the[ supported hardware page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI") which led me to the [PPA]("https://launchpad.net/~lexical/+archive/hwe-wireless") for my card

---

### Post by Bucky Ball on 2014-06-15
Can't help with this at the moment (need to go out), but I have changed the thread title to give you a better chance of specific help with that card. Getting it working should be do-able without much effort. Back later, but hopefully someone else will leap in before then. Good luck and welcome to the forums. ;)

---

### Post by GnowledgedGnome on 2014-06-15
To clarify the Atheros adapter is for my ethernet connection. I am having issues with my wireless connection (Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter)

---

### Post by Bucky Ball on 2014-06-16
Title fixed. It will appear as the title you see on the first post in all search lists. ;)

---

### Post by GnowledgedGnome on 2014-06-16
> **Bucky Ball said:**
> Title fixed. It will appear as the title you see on the first post in all search lists. ;)

Thank you for your help. I hope the forums will help me resolve this issue so I can be up and running Ubuntu soon.

---

