---
title: "Problems with BCM4315"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by edgar.federico on 2013-12-12
I am not being able to connect through the wireless in my BenQ Joybook Lite U105 with Ubuntu 13.10 with a chip BCM4315.
Somebody can give me a hand?
I have previously used ubuntu but not in this computer, so please be quite specific in your answers.
Thank you

---

### Post by edgar.federico on 2013-12-12
After the command 
lspci -nnk | grep -iA2 net

I get 

07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04ac]
    Kernel driver in use: b43-pci-bridge
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: COMPAL Electronics Inc Device [14c0:0047]
    Kernel driver in use: r8169


Is this of any use for you guys??

---

