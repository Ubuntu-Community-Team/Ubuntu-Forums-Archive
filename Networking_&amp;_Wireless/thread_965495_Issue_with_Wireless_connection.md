---
title: "Issue with Wireless connection"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by sidslasttheorem on 2008-10-31
Hey,

 I have a HP dv 5 that I got 2 days back and wanted to install ubuntu 8.10 on it to dual boot with vista.
 During the install from the live CD, the partitioning dialog box hung and replied that there was an error writing to disk (on a new comp!). So i hit exit and went through the same process.. only now it wasnt showing me a windows partition at all...
 I didnt really mind too much as I didnt have anything done on vista yet, so I went ahead with the installation. However, once it competed, I found that it wouldnt connect to the internet.
 I have a Intel Wireless 5100 AGN card. 
 While the available networks were shown, I couldnt connect to my network even though I entered the WEP key. The network manager kept bring up the dialog box repeatedly, without actually connecting.

the output of lspci gives :
```
02:00.0 Network Controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```

the output of sudo lshw -C network gives:
```

*-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:b2:8d:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=10.1.196.235 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:0b:fe:22
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:d8:7b:2b:26:9c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

output of ifconfig wlan0 is:
```

wlan0 
Link encap:Ethernet HWaddr 00:21:5d:b2:8d:a8
inet addr:10.1.196.235 Bcast:10.1.199.255 Mask:255.255.252.0
inet6 addr: fe80::221:5dff:feb2:8da8/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:792 errors:0 dropped:0 overruns:0 frame:0
TX packets:586 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:424200 (424.2 KB) TX bytes:76486 (76.4 KB)
```

Number of packets is because I was able to connect to a n/w that gave limited connectivity without having to provide authorization (basically a network that lets you open only one or two specific webpages to help you install something based on the info on those pages)

I tried to switch on/off the wireless connectivity button on the laptop. and also the check-box that appears for 'Enable Wireless' when you right-click on the networks icon in ubuntu.
Finally, the switch on the laptop is showing that the wireless is ON, and the check-box is ticked for 'Enable Wireless' in the GUI (right-clicking on networks icon - located top right by default)

Output of dmesg | grep -i iwlagn :

```

[529.735108] iwlagn: Radio Frequency Kill Switch is ON
[577.565998] iwlagn 0000:02:00:0: PCI INT A disabled
[588.697568] iwlagn 0000:02:00:0: PCI INT A -> GSI 16 (level, low) _> IRQ 16
[588.697687] iwlagn 0000:02:00:0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[4595.076782] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd_failed: -5
[4595.077958]iwlagn: Radio Frequency Kill Switch is ON
[...] iwlagn 0000:02:00:0: PCI INT A disabled
[...] iwlagn 0000:02:00:0: PCI INT A -> GSI 16 (level, low) _> IRQ 16
[...] iwlagn 0000:02:00:0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)

```

can anyone tell me whats going wrong?
I even checked my /lib/firmware for the ucode file for iwlwifi-5000, and copied it into the 2.6.27-7-generic folder, but nothing is changing

-siddharth

---

### Post by sidslasttheorem on 2008-11-01
bump

---

### Post by rabside on 2008-11-15
I have the same problem! pls help!

---

