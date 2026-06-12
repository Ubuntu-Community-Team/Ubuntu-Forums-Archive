---
title: "i40e AMD-Vi IO_PAGE_FAULT"
date: 2023-12-15
forum: Networking &amp; Wireless
---

### Post by oeffe4ever on 2023-12-15
Hello,

one of our servers crashes regularly (Ubuntu 22.04), apparently during heavy network load. The log files are then full of this message (with different addresses):

```
kernel: [514257.305733] i40e 0000:02:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0020 address=0x79ea8113f60 flags=0x0000]
```

This is the driver:

```

i40e: Intel(R) Ethernet Connection XL710 Network Driver
i40e: Copyright (c) 2013 - 2019 Intel Corporation.
i40e 0000:02:00.0: fw 8.5.67516 api 1.15 nvm 8.50 0x8000be1e 1.3295.0 [8086:15ff] [15d9:1c76]
i40e 0000:02:00.0: MAC address: 7c:c2:55:9d:d2:78
i40e 0000:02:00.0: FW LLDP is enabled
i40e 0000:02:00.0 eth0: NIC Link is Up, 10 Gbps Full Duplex, Flow Control: None
i40e 0000:02:00.0: PCI-Express: Speed 8.0GT/s Width x4
i40e 0000:02:00.0: PCI-Express bandwidth available for this device may be insufficient for optimal performance.
i40e 0000:02:00.0: Please move the device to a different PCI-e link with more lanes and/or higher transfer rate.
i40e 0000:02:00.0: Features: PF-id[0] VFs: 64 VSIs: 66 QP: 119 RSS FD_ATR FD_SB NTUPLE DCB VxLAN Geneve PTP VEPA
i40e 0000:02:00.1: fw 8.5.67516 api 1.15 nvm 8.50 0x8000be1e 1.3295.0 [8086:15ff] [15d9:1c76]
i40e 0000:02:00.1: MAC address: 7c:c2:55:9d:d2:79
i40e 0000:02:00.1: FW LLDP is enabled
i40e 0000:02:00.1: PCI-Express: Speed 8.0GT/s Width x4
i40e 0000:02:00.1: PCI-Express bandwidth available for this device may be insufficient for optimal performance.
i40e 0000:02:00.1: Please move the device to a different PCI-e link with more lanes and/or higher transfer rate.
i40e 0000:02:00.1: Features: PF-id[1] VFs: 64 VSIs: 66 QP: 119 RSS FD_ATR FD_SB NTUPLE DCB VxLAN Geneve PTP VEPA
i40e 0000:02:00.0 enp2s0f0: renamed from eth0
i40e 0000:02:00.1 enp2s0f1: renamed from eth1
i40e 0000:02:00.0: entering allmulti mode.

```

This message stands out there:

```

i40e 0000:02:00.1: PCI-Express bandwidth available for this device may be insufficient for optimal performance.
i40e 0000:02:00.1: Please move the device to a different PCI-e link with more lanes and/or higher transfer rate.

```

"modinfo i40e" shows:

```

filename:       /lib/modules/5.15.0-87-generic/kernel/drivers/net/ethernet/intel/i40e/i40e.ko
license:        GPL v2
description:    Intel(R) Ethernet Connection XL710 Network Driver
author:         Intel Corporation, <e1000-devel@lists.sourceforge.net>
srcversion:     263AAE07A824C74401C1729
...

```


Does somebody has any idea ? GRUB_CMDLINE_LINUX_DEFAULT="iommu=soft" is sometimes recommended in similar cases with IO_PAGE_FAULT. Maybe I should lower the speed from 10 Gbit/s to 1 Gbit/s as a test?

Thanks

Stefan

---

