---
title: "Ubunto 18.04 LTS - No Wifi Adapter Found"
date: 2018-05-01
forum: Networking &amp; Wireless
---

### Post by leocatto5 on 2018-05-01
Hello everyone, 

I've just started in the "Ubuntu World" and I did the dual boot of the newest version 18.04 aside to my Windows 10. 

The installation was successful but apparently I'm not able to connect via wireless. I can't see the "Wifi" icon on the top corner and when I go to Settings --> Wifi, 

the message "No Wifi adapter found" is displayed. 

I've been looking for solutions but wasn't very successful. 

When I type in the terminal : lspci-nnk | grep -iA3 net, it shows the following version: Qualcomm Atheros QCA9565/AR9565 Wireless Network Adapter.

Thank you, 

Leonardo.

---

### Post by gugra on 2018-07-08
I have this exact problem with the same card  and I'm also using ubuntu 18.04 alongside of windows 10 any help ?
[http://paste.ubuntu.com/p/dHC8F3Gby9/](http://paste.ubuntu.com/p/dHC8F3Gby9/)

---

### Post by deadflowr on 2018-07-08
*Thread moved to **Networking and Wireless***

---

### Post by praseodym on 2018-07-09
Please boot with the kernel parameter
```

iommu=soft
```
and report back

---

