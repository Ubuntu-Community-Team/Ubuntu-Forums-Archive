---
title: "Can't find my wireless device on Dell Latitude e6520"
date: 2020-04-20
forum: Networking &amp; Wireless
---

### Post by csg2 on 2020-04-20
I got this older labtop and installed Ubuntu. During install, the wireless device is detected. I even got it to work once from the install menu.

Once installed, I have no wireless and it doesn't show up in lspci. I figure it is just a matter of installing the right driver/firmware, but I have not had any luck with search engines.

The wireless-info.txt is here:
[https://pastebin.com/8uv17fK1](https://pastebin.com/8uv17fK1)

---

### Post by jeremy31 on 2020-04-20
Can you boot the Live Ubuntu and post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb
```

---

### Post by csg2 on 2020-04-21
The 6205 is the interface that worked during install.

I hadn't realized it was not a PCI device. Still I tried lsusb and didn't see it. 

```
ubuntu@ubuntu:~$ lspci -nnk | grep -iA3 net; lsusb
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    Subsystem: Dell 82579LM Gigabit Network Connection (Lewisville) [1028:0494]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0082] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1321]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
Bus 002 Device 005: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 004: ID 413c:8194 Dell Computer Corp. 
Bus 002 Device 003: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ 

```

---

### Post by csg2 on 2020-04-21
OK, I was confused. It's not a USB device. 

I booted into the machine again and tried the command.

```
root@Navigator:/home/csg2# lspci -nnk | grep -iA3 net; lsusb
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    Subsystem: Dell 82579LM Gigabit Network Connection (Lewisville) [1028:0494]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0082] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1321]
0a:00.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. 1394 OHCI Compliant Host Controller [1217:13f7] (rev 05)
    Subsystem: Dell 1394 OHCI Compliant Host Controller [1028:0494]
Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 413c:8194 Dell Computer Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Navigator:/home/csg2# 

```

So now at least the machine sees the device. Don't know why it does now and not before. 

But there is no kernel module and I can't access the wireless options in the networking menu. This is just a apt-get call now isn't it? If I can get the correct firmware for this chip?

---

### Post by jeremy31 on 2020-04-21
Use Driver Manager and remove the backport-iwlwifi-dkms and reboot

---

### Post by csg2 on 2020-04-21
If you mean the "Additional Driver" window, this always shows empty.

But, I had installed the iwlwifi via Aptitude and uninstalled it the same way. A quick reboot and Bam, wifi is working. I am writing this via the WiFi on the laptop. 

Thank you for your help!

---

