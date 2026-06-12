---
title: "HP Pavilion 15 Wireless on 15.04 Not Working"
date: 2015-08-12
forum: Networking &amp; Wireless
---

### Post by jimmy37 on 2015-08-12
Hi,

I would be very grateful if anyone can help me to get the onboard wifi card working on my HP Pavilion 15-p216na.

When the machine first boots, the wifi card itself is detected, confirmed via lspci (shown below) however it does not find any networks in the Network Manager GUI. I'm currently using a USB wifi card which does work properly.

```
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 08)
    Subsystem: Hewlett-Packard Company Device 2296
    Kernel driver in use: r8169

```

I can see here that the drive indicates it wants the 8101 driver, yet it is using the r8169 driver.

I tried to disable the r8169 to see if the wifi card would then switch to the 8101.

```

$ sudo modprobe -r r8169
$ sudo modprobe r8101

```

The output of lspci then shows that the wifi card is not using any driver

```
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 08)
    Subsystem: Hewlett-Packard Company Device 2296

```

I've managed to blacklist the r8169 module, so the onboard wifi card is now using the r8101 I downloaded and installed from realtek

```

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 08)
    Subsystem: Hewlett-Packard Company Device 2296
    Kernel driver in use: r8101

```

Disappointingly, there's no wireless interface appearing on iwconfig, and nor is there anything in dmesg that appears to be related to this. 

Unfortunately this is where my knowledge and expertise hits a brick wall and I don't know how to investigate further. I'll keep looking for an answer, but if anyone is kind enough to help that would make my day :).

---

### Post by chili555 on 2015-08-12
What you have shown us is not wireless at all. It is:> [COLOR="#FF0000"]Ethernet[/COLOR] controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast [COLOR="#FF0000"]Ethernet[/COLOR] controller (rev 08)Please run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by jimmy37 on 2015-08-12
Omg that's so embarrassing :biggrin:

```

&#10140;  ~  lspci -nn | grep 0280
08:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
&#10140;  ~  rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

---

### Post by jimmy37 on 2015-08-12
And the fix is to install [COLOR=#111111][FONT=Consolas]install bcmwl-kernel-source

[FONT=arial]Thanks for helping me... and making me look silly[/FONT][/FONT][/COLOR]

---

### Post by chili555 on 2015-08-12
> **jimmy37 said:**
> And the fix is to install [COLOR=#111111][FONT=Consolas]install bcmwl-kernel-source

[FONT=arial]Thanks for helping me... and making me look silly[/FONT][/FONT][/COLOR]May I assume it's now fixed?

No worries. We're glad it's working by whatever means.

---

