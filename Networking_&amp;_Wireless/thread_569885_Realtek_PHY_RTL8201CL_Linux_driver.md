---
title: "Realtek PHY RTL8201CL Linux driver"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by shinjukumaster on 2007-10-07
I have a Jetway mini-ITX board (Geode 1750) with an onboard RTL8201CL (10/100) and I&='m running EDGY LAMP server. How can I tell what driver/version is being used, and find an update for the driver if necessary? I have some network performance issues and want to make sure the driver is optimal.

---

### Post by noob12 on 2007-10-07
This command will tell you the device id of the card you have
```

lspci -nnvv

```

This will tell you what driver you have associated to the card.
```

sudo lshw -C network

```
Check the configuration line.

Using **modinfo** with that driver name will tell you what version of that driver you have.

---

