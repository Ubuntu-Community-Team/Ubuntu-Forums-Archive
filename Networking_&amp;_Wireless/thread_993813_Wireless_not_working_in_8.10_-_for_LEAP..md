---
title: "Wireless not working in 8.10 - for LEAP."
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Monarch2007 on 2008-11-26
I use Cisco LEAP for connecting to my office n/w under Windows; it works fine there. But under ubuntu, I simply can't get it up; had the same problem in previous releases. I was hoping that the latest release would fix it. But I don't see that happen.
Here is the excerpt from dmesg: Can someone help please?
Do I need to include any other logs?
Thanks and Regards.

[   19.381412] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   19.381416] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   19.381533] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.381548] iwl3945 0000:0c:00.0: setting latency timer to 64
[   19.381571] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   19.453088] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
[   19.466279] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.684455] iwl3945 0000:0c:00.0: PCI INT A disabled
[   37.037309] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   37.037465] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   37.040434] firmware: requesting iwlwifi-3945-1.ucode
[   37.160021] Registered led device: iwl-phy0:radio
[   37.160053] Registered led device: iwl-phy0:assoc
[   37.160119] Registered led device: iwl-phy0:RX
[   37.160137] Registered led device: iwl-phy0:TX
[   37.209422] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

