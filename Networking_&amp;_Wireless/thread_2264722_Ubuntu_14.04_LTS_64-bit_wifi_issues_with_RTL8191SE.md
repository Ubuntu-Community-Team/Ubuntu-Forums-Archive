---
title: "Ubuntu 14.04 LTS 64-bit wifi issues with RTL8191SEvA"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by jmrd0001 on 2015-02-09
Hi, I just installed 14.04 LTS 64-bit on an HP G62 and the wifi keeps dropping. 

Attached is the output from the wireless_script.

I tried a few things but I suspect I have the wrong driver. I see the drivers in use don't match the model exactly:
```

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. [COLOR=#ff0000]RTL8191SEvA[/COLOR] Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel driver in use: [COLOR=#ff0000]rtl8192se[/COLOR]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. [COLOR=#ff0000]RTL8101E/RTL8102E[/COLOR] PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: [COLOR=#ff0000]r8169[/COLOR]

```

Many thanks for your help !

---

