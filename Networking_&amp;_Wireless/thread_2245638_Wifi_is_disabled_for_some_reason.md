---
title: "Wifi is disabled for some reason"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by Adib_Valandri on 2014-09-25
hey, i 'm using ubuntu 14.04 right now. Fresh installation the Wireless is still connected. But after several days my wireless is not existed anymore. i'm searching in the forum, they said every wireless has it's own problems. can anyone help me?

this is my lspci
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fdd0]
    Kernel driver in use: atl1c

---

### Post by h.hittini on 2014-09-25
Let's see if the driver is still installed correctly
```
sudo lshw -C network
```

---

### Post by praseodym on 2014-09-25
Thats the LAN device. Please show
```

lsusb
pccardctl info
```

---

