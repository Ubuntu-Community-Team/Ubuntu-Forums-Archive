---
title: "USB Network adapter in order"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by patyala on 2007-04-03
Hello guys,
I have an USB network adapter, and I have a CAD software license related to this adapter MAC-address. As I starting to install this CAD software on Ubuntu 6.10 it takes the MAC-address of my first adapter, which is integrated on the motherboard, but I would like to use the USB adapter, how can I change the adapters order in Linux, especially in Ubuntu 6.10. In Windows XP it was easy with registry editor.
All possible solution is welcomed, except hacking the license. :)

Thank you in advance,
patyala

---

### Post by patyala on 2007-04-04
Let me answer my question:
with ifconfig you can "shut down" the interface you don't use:

```
ifconfig eth0 down
```

so the installer is just working fine now.
Maybe [this]("http://www.faqs.org/docs/linux_network/x-087-2-iface.interface.html") is useful for others too.

Bye,

Patyala

---

