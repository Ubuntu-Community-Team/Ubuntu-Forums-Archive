---
title: "lsusb doesn't list bluetooth driver"
date: 2021-09-23
forum: Networking &amp; Wireless
---

### Post by zoro98 on 2021-09-23
Hi Community,

I have dualbooted my laptop with windows10 and Ubuntu.

Ubuntu cannot sense my Bluetooth driver and hence I cannot use it. On the other hand Windows can run bluetooth without any issues.

Result of lsusb:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:0c00 Elan Microelectronics Corp. ELAN:ARM-M4
Bus 001 Device 002: ID 13d3:56c9 IMC Networks HP TrueVision HD Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```

I downloaded a bluetooth manager on Ubuntu but it gives the following   message : > Connection to BlueZ failed. BlueZ daemon is not   running, blueman manager cannot continue. This probably means that there   were no Bluetooth adapters detected or Bluetooth daemon was not   started. 

System specifications:
```

Model : HP laptop 15s - du0xxx
BIOS  Mode: UEFI
Wifi Adapter: Realtek RTL8723DE
[highlight]Network settings: [URL="https://pastebin.com/d5L9pWmL"]https://pastebin.com/d5L9pWmL
[/URL][/highlight]

```

Thank you for your time.

---

