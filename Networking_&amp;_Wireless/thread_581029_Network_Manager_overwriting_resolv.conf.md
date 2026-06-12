---
title: "Network Manager overwriting resolv.conf"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by dr_gonzo on 2007-10-19
I've upgraded to Gutsy Gibbon but this was also a problem in Fiesty Fawn. My network manager keeps overwriting my DNS settings in resolv.conf. 

Even when I use the network manager to enter my DNS details, a few minutes later, network manager seems to overwrite them with my router's IP. 

Does anyone know what the problem is here? It's really frustrating to have to enter my dns details every few minutes...

---

### Post by dr_gonzo on 2007-10-19
Found a workaround. I opened /etc/dhcp3/dhclient.conf 

Uncommented the line that starts with "#prepend domain-name-servers" and added my DNS server to it. Then did: sudo /etc/init.d/dhcdbd restart

---

### Post by mfyahya on 2008-02-29
That didn't work for me. But there's another workaround, if you're using the ext2 filesystem, use the chattr command to make /etc/resolv.conf immutable, so no process can change it
```

$ sudo chattr +i /etc/resolv.conf

```
now even root can't change the file until that attribute is removed.

---

