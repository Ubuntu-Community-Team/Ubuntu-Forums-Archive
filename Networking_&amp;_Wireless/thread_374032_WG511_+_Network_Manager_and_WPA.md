---
title: "WG511 + Network Manager and WPA"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by cr4z3d on 2007-03-02
Hello, I'm using Edgy and everything installed fine on my HP pavilion ze4200 laptop, including my Netgear WG511v1 wireless card. 

 The question I have, is that I'm not able to connect to my WPA home network. I read the sticky about setting up WPA, but is it possible to use network manager with WPA?

---

### Post by Floppyjoe on 2007-03-02
Network manager works with WPA on my laptop using my home network. I'm not sure if you still need to set up the WPA configuration file though. You probably do have to.

---

### Post by wieman01 on 2007-03-02
> **cr4z3d said:**
> Hello, I'm using Edgy and everything installed fine on my HP pavilion ze4200 laptop, including my Netgear WG511v1 wireless card. 

 The question I have, is that I'm not able to connect to my WPA home network. I read the sticky about setting up WPA, but is it possible to use network manager with WPA?
Simply go for Network Manager... There is no need to temper with text files if you choose to install it. The Sticky is there for Network Manager's lack of support for Static IPs.

---

### Post by cr4z3d on 2007-03-02
I have Network Manager already installed but when choosing my network i only have options for WEP

EDIT: The card is a Prism Duette based chip I believe. Here's some info i get when I do lspci -v

```

02:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
        Subsystem: Netgear WG511 Wireless Adapter
        Flags: bus master, medium devsel, latency 80, IRQ 5
        Memory at 22000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [dc] Power Management version 1

```

---

