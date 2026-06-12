---
title: "Intel 5350 AGN random freezes"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by mac-duff on 2014-04-30
Hi there,
some months ago I bought a Intel 5350 AGN wifi card for my old Dell Latitude D630 laptop and since then I get a lot of random freezes with 14.04 as well as with 13.10.

I tried the iwlwifi-5000-ucode-8.83.5.1 driver from [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi) , copied the iwlwifi-5000-5.ucode to /lib/firmware and regarding the lshw -class network command it seems also to be loaded when I double-check the firmware version.

```

*-network               
       description: Wireless interface
       product: PRO/Wireless 5350 AGN [Echo Peak] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:eb:05:b4:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=8.83.5.1 build 33692 ip=192.168.11.45 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:f6cfe000-f6cfffff

```

I also changed it to an network only but no difference. The speed and so is fine, it is just that out of nothing I have to do a hard reboot.

Any suggestions please?

Thanks
md

---

