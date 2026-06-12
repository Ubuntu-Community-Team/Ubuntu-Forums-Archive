---
title: "DHCP works - can't access web?"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2007-03-10
Hi

I'm wiring the house at the moment, as the wireless works rather slowly downstairs. 

I'm using standard ethernet cable and RJ-45 plugs, which seem to be the same as I have had all along... duh. 

So I connect all the little wires according to their nice bright colours, stick them in the connector and crimp it. Upon testing the cable, I get a DHCP connection
> DHCPACK from 192.168.0.1
bound to 192.168.0.104 -- renewal in 230072 seconds.

but when I try to access the web, I can't. Server not found and such, as if I had not connected at all. The second line of ifconfig (relating to eth0, my ethernet port:
```

inet addr:192.168.0.104 Bcast:192.168.0.255 Mask:255.255.255.0

```

That would suggest that I have connected to the network, right? 

firefox->world: server not found
firefox->router: timeout
ping->world: unknown host
ping->router: sendmsg: Operation not permitted, 100% loss. 

any ideas? A factory made cable works fine, and I can't see what could be wrong with mine. I copied right off one that works perfectly!

Thanks,
-K

---

### Post by Kulgan on 2007-03-10
update:

I now can't connect using any cables. Booted Fedora and it works, so it can't be the cable. WT*?? I guess this is a reinstall then. At least all my important ~/.* files were only symlinked to the FC partition :/

---

