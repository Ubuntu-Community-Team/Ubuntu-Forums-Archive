---
title: "[SOLVED] Ralink rt5390r"
date: 2022-07-06
forum: Networking &amp; Wireless
---

### Post by giuseppevenditti on 2022-07-06
Hi all,

I have an old HP Pavilion 20 with XFCE Ubuntu 20.04.4 LTS kernel 5.4.0-121-generic; wifi doesn't work: this is lshw:

```

*-pci:3
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:fea00000-feafffff
           *-network DISABLED
                description: Wireless interface
                product: RT5390R 802.11bgn PCIe Wireless Network Adapter
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlp4s0
                version: 00
                serial: a4:17:31:47:a6:55
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci  driverversion=5.4.0-121-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:fea00000-fea0ffff 

```

with Windows it works; any suggest?
Many thanks in advance

beppe

---

### Post by chili555 on 2022-07-06
Let's see if we can find out why it's disabled. Please run and post:

```
rfkill list all
sudo dmesg | grep -i rt2
```

---

### Post by giuseppevenditti on 2022-07-07
thanks for the replay

```
igas@hp-20-b100el:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

and

```
igas@hp-20-b100el:~$ sudo dmesg | grep -i rt2
[sudo] password di igas: 
[   19.430017] rt2800pci 0000:04:00.0: enabling device (0100 -> 0102)
[   19.430498] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   19.459838] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   20.087284] rt2800pci 0000:04:00.0 wlp4s0: renamed from wlan0

```

---

### Post by chili555 on 2022-07-07
> Hard blocked: [COLOR="#FF0000"]yes[/COLOR]That suggests that the wireless switch or key combination is set to disable the wireless radio. Please find it and switch it.

---

### Post by giuseppevenditti on 2022-07-07
yes, this is a clue, but the desktop hasn't some FX to press; I don't know where search;  but in windows mode it works
many thanks

---

### Post by chili555 on 2022-07-07
Please check here: [https://kaas.hpcloud.hp.com/pdf-public/pdf_3941897_en-US-1.pdf](https://kaas.hpcloud.hp.com/pdf-public/pdf_3941897_en-US-1.pdf)

> You can control the wireless devices in your computer using one or both of these features.
&#9679; Airplane mode key (also called wireless button or wireless key)

```
lsmod
```

> in windows mode it worksThat only shows that the hardware is not defective. In fact, a great many things work perfectly in Linux but not Windows and vice-versa.

---

### Post by giuseppevenditti on 2022-07-08
Many thanks chili555, now it works, I restarted without cable, may be some command that you suggested ... :P:P:P

---

