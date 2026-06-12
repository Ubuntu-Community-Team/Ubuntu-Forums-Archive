---
title: "Network Disabled - RfKill hardblocked"
date: 2014-11-24
forum: Networking &amp; Wireless
---

### Post by sruthi_kotamraju on 2014-11-24
I am new to ubuntu and I have recently installed a dual boot ubuntu 12.04 along with windows 7. But I am unable to connect to a Wi-Fi network. 

This is the output of 

```
lshw -C network :


  *-network
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:1f:af:2b:58:65
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.13-3 latency=0 multicast=yes port=twisted pair
       resources: irq:43 memory:f7e00000-f7e1ffff memory:f7e39000-f7e39fff ioport:f080(size=32)
  *-[COLOR=#ff0000]network DISABLED[/COLOR]
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:ca:af:1e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.7+ firmware=8.24.2.12 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:f7d00000-f7d01fff

rfkill list all


0: phy0: Wireless LAN
    Soft blocked: no
    [COLOR=#ff0000]Hard blocked: yes[/COLOR]

Dmesg | grep -i iwl


[   24.250946] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   24.250948] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   24.250969] iwlagn: connector callback registered
[   24.251093] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   24.251094] iwlwifi 0000:03:00.0: pci_resource_base = f8b78000
[   24.251095] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[   24.251382] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   24.254733] iwlwifi 0000:03:00.0: loaded firmware version 8.24.2.12
[   24.254822] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   24.254824] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   24.254826] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   24.254827] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   24.254829] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   24.254831] iwlwifi 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   24.254943] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   24.255390] iwlwifi 0000:03:00.0: [COLOR=#ff0000]RF_KILL bit toggled to disable radio.[/COLOR]
[   24.279134] iwlwifi 0000:03:00.0: device EEPROM VER=0x120, CALIB=0x4
[   24.279135] iwlwifi 0000:03:00.0: Device SKU: 0xF0
[   24.279137] iwlwifi 0000:03:00.0: Valid Tx ant: 0x7, Valid Rx ant: 0x7
[   24.279144] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   24.300394] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
```


My laptop does not have a hardware switch ( so that couldn't have sent RfKill hardblock) . 
Also I have tried Fn+F2 which does not seem to work.
Can somebody please help me? I really don't know what to do next.

Thanks

---

### Post by chili555 on 2014-11-24
What brand and model of laptop is it? May we see:```
lsmod
```Thanks.

---

### Post by wildmanne39 on 2014-11-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

