---
title: "[SOLVED] Ubuntu 16 network DISABLED Qualcomm Atheros"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by stef-struijk on 2016-04-20
I'm on Ubuntu 16 and just did '*sudo apt-get update*' and '*sudo apt-get dist-upgrade*'.
My wired connection works, but my WiFi-networks shows **'device not ready'**.

```
sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 32
       serial: ??:??:??:??:??:?? (hidden for privacy)
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-21-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:127 memory:df200000-df3fffff

```

From '**network DISABLED**' it seems I need to enable my wireless network, but I don't know how.
In ' Network' WiFi is set to 'ON'.

```
rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
Also I don't have any hardware switch on my Laptop to turn on/off wireless.
```
dmesg | grep wlan
[    6.521248] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    6.592877] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[  108.831749] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[  113.386692] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[  116.774551] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[  130.405116] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[  133.788589] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[  147.374607] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[  150.754970] ath10k_pci 0000:03:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
```

[B][SIZE=2]Question:
[/SIZE][/B][SIZE=2]How do I enable my wireless?

[/SIZE]**[SIZE=2]p.s.  [/SIZE]** [SIZE=2]After '*sudo apt-get dist-upgrade*' I could find 1 Wireless network (although I'm surrounded by many), but after turning Wi-Fi on and off in 'Network', I get **'device not ready'**. [/SIZE]

---

### Post by stef-struijk on 2016-04-24
I found the solution here: [http://askubuntu.com/questions/607707/ath10k-installation](http://askubuntu.com/questions/607707/ath10k-installation)

It was a driver problem, which is solved by updating the drivers with the files here: [https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174](https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174)

---

