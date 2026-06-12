---
title: "How do I set up a static IP in Ubuntu?"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by mjpatey on 2006-09-02
Hi, all-

My Ubuntu machine dual-boots with Windows, and exists on a network that includes two other Windows machines.  I'd like each machine to have a static IP address (in my case, 192.168.1.xxx).  I don't care if the external IP address is static, just the internal one the router uses to address each computer on the LAN.

I have instructions on how to set up each Windows box to have its own static IP, but I assume that configuring my machine to have a static IP while in Windows would have no effect on that same machine when it's in Ubuntu.

Assuming this is true... does anybody know how to do it in Ubuntu?  I couldn't find any tutorials out there for it.

Thanks for any help you may have!

-Mark

---

### Post by Iowan on 2006-09-02
System>Administration>Networking>Ethernet Connection>Properties.From there you should be able to set configuration to Static and set IP address, Subnet mask, and Gateway address.

From a terminal, you can edit the /etc/network/interfaces file. Should look something like:```
# The primary network interface
iface eth0 inet static
        address 192.168.1.9
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

```

---

### Post by az on 2006-09-02
> **mjpatey said:**
> Hi, all-

My Ubuntu machine dual-boots with Windows, and exists on a network that includes two other Windows machines.  I'd like each machine to have a static IP address (in my case, 192.168.1.xxx).  I don't care if the external IP address is static, just the internal one the router uses to address each computer on the LAN.

-Mark

System - Administration - Networking and then pick you interface and see the screenshot below:

---

### Post by mjpatey on 2006-09-02
Wow, thanks for taking the time!  I appreciate the help.  As soon as I get home tonight, I'll set it up.

These forums absolutely ROCK.

---

