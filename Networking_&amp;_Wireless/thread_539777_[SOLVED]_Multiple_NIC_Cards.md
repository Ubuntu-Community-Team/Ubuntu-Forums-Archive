---
title: "[SOLVED] Multiple NIC Cards"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by Sonthun on 2007-08-31
Hi.  I've got an onboard NIC and a PCI NIC on a new Ubuntu installation.  Ubuntu detects both of them, but for some reason the Network manager will only activate one of them at a time.  I have to physically click on the other to get it enabled.  How can I get both cards to activate upon boot?  Thanks.

---

### Post by Sonthun on 2007-09-07
Is this just not possible?  I've been trying to learn how to manually configure the network, but that is quite the mountain to climb.

Thanks.

---

### Post by noob12 on 2007-09-07
They should both activate on boot if you have **auto** and **iface** lines specifying their configuration in /etc/network/interfaces.  If you have not specified them there, they are in roaming mode and NM will only enable one at once.

See **man interfaces**.  

If you have a totally stationary wired installation, and you find it keeps interfering, you can just remove NetworkManager.  It doesn't really add any value in that situation.

---

### Post by Sonthun on 2007-09-08
Thanks.  Disabling Network manager was the key.  For those looking how to disable Network manager go to: [https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

---

### Post by DarkAgdistis on 2007-10-11
And how do you tell an application to use one specific NIC and another application to use another NIC ?? :confused:

---

