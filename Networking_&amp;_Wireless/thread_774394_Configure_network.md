---
title: "Configure network?"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by kbbn on 2008-04-29
How do i configure my network on a ubuntu server?

netconfig does not work, and network-admin requires x...

Hope someone can help me :-/

---

### Post by amingv on 2008-04-29
You can manually modify your /ect/network/interfaces file or use commands such as ifconfig or iwconfig (for wireless networks); the setup depends on how you want to configure it.
For more info:

```
man interfaces
man ifconfig
man iwconfig
```

---

### Post by kbbn on 2008-04-29
Cool, thx a lot :-)

---

