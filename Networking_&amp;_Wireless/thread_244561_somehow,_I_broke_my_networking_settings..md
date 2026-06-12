---
title: "somehow, I broke my networking settings."
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by loopjeremyloop on 2006-08-26
don't ask how.  I don't know.  I think it was from when I was trying to get my 3g card by verizon working, and one of the many howtos out there had a command that stripped my default gateway...


aaaanyway
I go into the network manager app, and it shows my two nics (wireless and wired), the wireless connects just fine to my home network, too... but the gateway is blank.  I can't seem to add a default gateway.  Any suggestions on how to do so?  

I once used the route command, when i was into gentoo, but wasn't able to figure it out for my dhcp network.  

Thanks in advance!

---

### Post by Woei on 2006-08-26
> **loopjeremyloop said:**
> don't ask how.  I don't know.  I think it was from when I was trying to get my 3g card by verizon working, and one of the many howtos out there had a command that stripped my default gateway...


aaaanyway
I go into the network manager app, and it shows my two nics (wireless and wired), the wireless connects just fine to my home network, too... but the gateway is blank.  I can't seem to add a default gateway.  Any suggestions on how to do so?  

I once used the route command, when i was into gentoo, but wasn't able to figure it out for my dhcp network.

As root, type in 'dhclient3 eth0', or whatever your active NIC is. Then type in 'route' to find the default gateway.

The command to add a default gateway is
```

sudo route add default gw 192.168.1.1

```

Of course, the IP address might be something else, but it's usually .1 or .254 of the network you currently have an IP address in.

---

