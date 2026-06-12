---
title: "Unable to find a wifi domestic network"
date: 2020-05-16
forum: Networking &amp; Wireless
---

### Post by josir on 2020-05-16
Ubuntu 14.04 is not recognizing my domestic Wifi network.

I think it's **not** a hardware or drive problem because the system works fine with routed cell phones, external networks but not in this specific network. In fact, the network even appears on the avaialable wifi list.

The local network also works fine with cell phones.

I tried:

```
sudo iwlist scan | grep ESSID
```

but the network does not appear.

I tried also to configure the wifi manually but it didn't work either.

The driver and hardware is working fine but here is the specification in order to get some clue:

```

lspci -knn | grep Net
07:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter

```

How can I debug or find what is wrong with my ubuntu configuration?

---

