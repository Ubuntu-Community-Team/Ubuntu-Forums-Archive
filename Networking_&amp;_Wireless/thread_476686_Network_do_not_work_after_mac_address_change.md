---
title: "Network do not work after mac address change"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Vautomation on 2007-06-17
Hi
Network do not work after mac address change with ifconfig or other tool, and I can not set it at boot time

---

### Post by Vautomation on 2007-06-18
Is abybody here???

---

### Post by Mr. C. on 2007-06-18
Can you describe your network connections?

Run below before/after change and show results:
```

ifconfig -a
arp -a

```
MrC

---

### Post by Vautomation on 2007-06-18
Hello MrC
Thank you for your reply!
My NIC is realtek RTL8111B PCI-E Gb LAN and use r8169 linux driver from ubuntu 7.04  64 bit
As before as well after ifconfig and arp returns the same result with only difference MAC address.
interface is up and running in both cases, but when with fake MAC netwotk is not working.(before have ping to gw, after have not ping to gw)
I tried to set fake MAC at boot time but with no success.

---

### Post by Mr. C. on 2007-06-18
I asked you to show the output, so that I can interpret the results.  Evidence is more useful than your interpretation.  Show the output.

Did you clear the arp entry ?

MrC

---

