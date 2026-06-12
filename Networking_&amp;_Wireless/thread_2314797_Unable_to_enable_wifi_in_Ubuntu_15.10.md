---
title: "Unable to enable wifi in Ubuntu 15.10"
date: 2016-02-23
forum: Networking &amp; Wireless
---

### Post by juanjose-casanova on 2016-02-23
Hi, I've updated to 15.10 and the WIFI stopped working.
I'm getting this:

```

$sudo lshw -class network
  *-network DISABLED      
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: bb
       serial: ac:fd:ce:9a:b7:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-27-generic firmware=25.30.13.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn

```

Then if I try with rfkill I get:

```

$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

Finally I found this:

```

$ dmesg | grep -e rt2 -e 0000:01:00.0
[    0.175612] pci 0000:01:00.0: [8086:08b1] type 00 class 0x028000
[    0.175801] pci 0000:01:00.0: reg 0x10: [mem 0xf7c00000-0xf7c01fff 64bit]
[    0.176202] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.176268] pci 0000:01:00.0: System wakeup disabled by ACPI
[   11.863804] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
[   11.908561] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2
[   11.974235] iwlwifi 0000:01:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[   12.616301] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   12.616412] iwlwifi 0000:01:00.0: L1 Enabled - LTR Disabled
[   12.616807] iwlwifi 0000:01:00.0: RF_KILL bit toggled to disable radio.
[   12.616857] iwlwifi 0000:01:00.0: L1 Enabled - LTR Disabled
[   12.928025] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0

```

I'm not sure how to solve those "Direct firmware load for iwlwifi-7260-15.ucode failed with error -2".

Any Help?
Thanks in advance!

---

### Post by berk6 on 2016-02-24
You may need to reinstall your WIFI driver since when kernel updates, things tend to override and havoc occurs. I had a similar problem on Arch with my Broadcom WIFI card, but looks like you have an Intel one. 

Don't Intel WIFI cards work great out of the box?

---

