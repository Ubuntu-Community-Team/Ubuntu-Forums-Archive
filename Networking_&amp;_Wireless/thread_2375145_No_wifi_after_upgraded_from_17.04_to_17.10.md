---
title: "No wifi after upgraded from 17.04 to 17.10"
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by roma.parabellum on 2017-10-22
Hi!
Guys, I am here with the same problem - no wi-fi after upgrade to 17.10.
I downloaded script for collecting info, transferred it to Ubuntu decktop folder via usb-flash drive, but as it runs it produces only one row only - "...wi-fi info START...", the rest of the file is empty...
Tip in post 4 above did not help (
Could you help me please?

---

### Post by jeremy31 on 2017-10-22
Split from [https://ubuntuforums.org/showthread.php?t=2375063](https://ubuntuforums.org/showthread.php?t=2375063)
Please provide results from terminal for ```
lspci -nnk | grep -iA3 net; rfkill list
```

---

### Post by roma.parabellum on 2017-10-22
Here is the result:
```
03:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Wireless 8260 [8086:1010]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7970]
    Kernel driver in use: r8169
    Kernel modules: r8169
05:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 03)
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by jeremy31 on 2017-10-22
Does wifi connect to the router?  If it does try ```
ping -c3 8.8.8.8
```

---

### Post by roma.parabellum on 2017-10-22
All packets are OK.

---

### Post by cameronfra@gmail.com on 2017-10-22
Suffering similar post upgrade to 17.10 from 17.04; however I have intranet but no internet.
Other devices have not issue accessing external, such as current one I am using...???

---

### Post by jeremy31 on 2017-10-22
I would edit the connection in Network Manager and add 8.8.8.8 for an additional DNS then reboot

Then look at [https://ubuntuforums.org/showthread.php?t=2374857&p=13700631#post13700631](https://ubuntuforums.org/showthread.php?t=2374857&p=13700631#post13700631)

---

### Post by cameronfra@gmail.com on 2017-10-22
Cheers!
resolvconf reconfigure to the rescue

---

### Post by roma.parabellum on 2017-10-22
Great!
This advice [https://ubuntuforums.org/showthread....1#post13700631]("https://ubuntuforums.org/showthread.php?t=2374857&p=13700631#post13700631") works!
Thank you very much!

---

