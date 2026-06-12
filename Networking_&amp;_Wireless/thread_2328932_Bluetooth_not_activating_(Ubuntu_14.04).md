---
title: "Bluetooth not activating (Ubuntu 14.04)"
date: 2016-06-25
forum: Networking &amp; Wireless
---

### Post by Mayara on 2016-06-25
[SIZE=3]I have exactly the same issues of the OP, I looked at the suggestions on fixing this, but I'm not being very successful.

Could someone take a look on this? 

Thanks!

lspci:

```
mayara@mayara:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)


```

lsusb:

```
mayara@mayara:~$ lsusb
Bus 002 Device 099: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1008  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```[/SIZE]

---

### Post by wildmanne39 on 2016-06-25
Moved to networking for better help. Please do not post in old threads!
Thanks

---

### Post by praseodym on 2016-06-26
modprobe -c | grep -i "0cf3.*3004"
```
alias usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in* [COLOR="#FF0000"]ath3k[/COLOR]
```
Should work ootb:
```

sudo modprobe -v ath3k
dmesg | egrep 'ath|blue|firm|error|fail'
```

---

### Post by jeremy31 on 2016-06-26
What kernel is being used? ```
uname -a
```

I know a timing fix for xhci and the ath3k module was merged into the 3.16 kernel but I don't know if it was ever included in the 3.13 kernel

---

