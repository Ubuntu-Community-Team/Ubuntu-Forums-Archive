---
title: "Problem with WLAN after woke up from suspension - Samsung ATIV Book 4 (NP450R4E)"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by holybeefy on 2014-05-24
Model: Samsung ATIV Book 4 (NP450R4E)
OS: Ubuntu 14.04

[U][B]WLAN driver:
[/B][/U]
[FONT=courier new]       description: Wireless interface[/FONT]
[FONT=courier new]       product: [COLOR=#ff0000]AR9485 Wireless Network Adapter[/COLOR][/FONT]
[FONT=courier new]       vendor: Qualcomm Atheros[/FONT]
[FONT=courier new]       physical id: 0[/FONT]
[FONT=courier new]       bus info: pci@0000:02:00.0[/FONT]
[FONT=courier new]       logical name: wlan0[/FONT]
[FONT=courier new]       version: 01[/FONT]
[FONT=courier new]       width: 64 bits[/FONT]
[FONT=courier new]       clock: 33MHz[/FONT]
[FONT=courier new]       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless[/FONT]
[FONT=courier new]       configuration: broadcast=yes driver=ath9k [COLOR=#ff0000]driverversion=3.13.0-24-generic[/COLOR] firmware=N/A ip=192.168.1.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn[/FONT]
[FONT=courier new]       resources: irq:16 memory:f7900000-f797ffff memory:f7980000-f798ffff[/FONT]

_**Problem:**_

Closing the lid suspended the laptop, and re-opening it and woke up, the wireless LAN cannot be activated:

[FONT=courier new]$ rfkill list[/FONT]
[FONT=courier new]0: phy0: Wireless LAN[/FONT]
[FONT=courier new]    Soft blocked: no[/FONT]
[FONT=courier new]    Hard blocked: yes[/FONT]
[FONT=courier new]1: hci0: Bluetooth[/FONT]
[FONT=courier new]    Soft blocked: no[/FONT]
[FONT=courier new]    Hard blocked: no[/FONT]

[U][B]Question:
[/B][/U]
I've tried many methods, including rfkill unblock, modprobe, nm-tool, the wireless LAN cannot be activated. I've checked Network Manager, and it should be waken up properly (since wired connection is not affected).

I've read there are many problems with this driver in Asus notebook, but I don't think their solution can be applied to Samsung. Any idea? Any more other methods to re-activate the driver beside the above?

---

### Post by praseodym on 2014-05-25
Hi,

force the driver being unloaded during suspend/hibernate and reloaded during wake-up:

```
sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module
echo 'SUSPEND_MODULES="$SUSPEND_MODULES ath9k" ' | sudo tee /etc/pm/config.d/00sleep_module
```

---

### Post by holybeefy on 2014-06-01
Thanks but it didn't work. I'm checking the log and trying other methods.

---

### Post by Alpex on 2015-02-21
> **holybeefy said:**
> Thanks but it didn't work. I'm checking the log and trying other methods.

I have the same laptop and exactly same problem. Any news or workarounds?

---

