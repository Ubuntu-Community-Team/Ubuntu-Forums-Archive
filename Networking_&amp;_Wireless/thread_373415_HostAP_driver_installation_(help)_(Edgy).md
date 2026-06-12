---
title: "HostAP driver installation (help?) (Edgy)"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by JonnyTrombone on 2007-03-01
I've been trying to install the HostAP drivers in Edgy. I've downloaded the drivers, extracted them, and set my kernel path in the Makefile:
```
KVERS ?= $(shell uname -r)
KERNEL_PATH ?= /lib/modules/2.6.17-11-386
```

When I run Make, however, I get the following:
```
/home/smokey/hostap-driver-0.4.9/Makefile:28: /lib/modules/2.6.17-11-386/.config: No such file or directory
/home/smokey/hostap-driver-0.4.9/Makefile:46: WARNING: No kernel PCMCIA support found and PCMCIA_PATH is not defined
/home/smokey/hostap-driver-0.4.9/Makefile:53: WARNING: Linux wireless extensions, CONFIG_NET_RADIO, not enabled in the kernel
make: *** No rule to make target `/lib/modules/2.6.17-11-386/.config'.  Stop.

```

The Read-me that comes with the drivers (also found at [www.hostap.epitest.fi](www.hostap.epitest.fi)) doesn't help at all. 

Any instructions would be great.

---

