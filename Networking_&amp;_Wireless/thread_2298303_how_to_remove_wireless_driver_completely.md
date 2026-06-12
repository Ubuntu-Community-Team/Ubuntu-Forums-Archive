---
title: "how to remove wireless driver completely?????"
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by Hasan55 on 2015-10-10
hey guys .........
i want to completely remove my wireless broadcom (wifi) driver but i don't know how to do it please advice.....
For your knowlege i am giving my wifi card informission.

root@Ananymous:~# lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx] [1002:5a3f]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller [1002:4374]
00:13.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller [1002:4375]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge [1002:4371]
00:14.5  Multimedia audio controller [0401]: Advanced Micro Devices, Inc.  [AMD/ATI] IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0  Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8  [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS480M [Mobility Radeon Xpress 200] [1002:5955]
05:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
[COLOR=#400000]05:02.0  Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One  54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031][/COLOR]
root@Ananymous:~#

---

### Post by Bucky Ball on 2015-10-10
*Thread moved to **Networking & Wireless**.*

Please use code tags. Please see the last link in my signature. Thanks.

---

### Post by Hadaka on 2015-10-10
Hi, to prevent your wireless card from loading please copy and paste..
```
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

*To restore....please do..
```
sudo sed -i '/^b43/ d' /etc/modprobe.d/blacklist.conf
```


The first command blacklists and places your b43 dirver (wireless driver) into -> /etc/modprobe.d/blacklist.conf

The second command removes the blacklisted b43 driver (wireless driver) from -> /etc/modprobe.d/blacklist.conf

---

### Post by Hasan55 on 2015-10-12
thanks all i have solve this problem............................

---

### Post by Bucky Ball on 2015-10-12
Good news. Please see the first link in my signature. Good luck. :)

---

### Post by Hadaka on 2015-10-12
Great ! please sign back in to your thread then click TOOLS
and mark this thread SOLVED
thanks

---

