---
title: "weird knetworkmanager problem"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by PixelCloud on 2006-08-28
using wifi-radar, or the default wireless configuration tool(kwifimanager) in kubuntu i have no issues connecting to my wireless network (using ndiswrapper), however when i try to connect to my network using Knetworkmanager, it hangs at "activation stage: configuring device" then fails to connect to the network...


any ideas?

---

### Post by ltmon on 2006-08-28
Whilst trying to connect type this into a Konsole:
```

tail -f /var/log/syslog

```
It should give some info as to what's going on.

Also do some searches for "NetworkManager" and your wireless chipset... there might be known problem and workaround.

L.

---

