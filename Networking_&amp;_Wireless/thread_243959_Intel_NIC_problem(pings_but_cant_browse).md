---
title: "Intel NIC problem(pings but cant browse)"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by GCR on 2006-08-25
Hey! I have a problem with Ubuntu. I have a Intel 845 chipset and Ubuntu loads the module and everything. 

Howveer I cant browse the web. I can though, ping to any address, but once I pop up Firefox to browse the web, it wont do anything? What could this be from?

Ive tried lading/unloading both the e100 and e100pro drivers but to no avail? Any help?

---

### Post by Woei on 2006-08-26
> **GCR said:**
> Hey! I have a problem with Ubuntu. I have a Intel 845 chipset and Ubuntu loads the module and everything. 

Howveer I cant browse the web. I can though, ping to any address, but once I pop up Firefox to browse the web, it wont do anything? What could this be from?

Ive tried lading/unloading both the e100 and e100pro drivers but to no avail? Any help?

How do you get an IP address ? Statically, through DHCP ? It sounds to me like your DNS servers are not configured in /etc/resolv.conf. Contact your ISP for their DNS server IPs, or maybe enter the IP of your NAT/router, as most of them have a small caching DNS server running. Just add the entries at the bottom of the /etc/resolv.conf file with something like
```

nameserver 192.168.0.1

```

Alternatively, it's possible your ISP requires you to access HTTP servers through a proxy. Again, ask your ISP if this is the case, and configure the proxy in System -> Preferences -> Network proxy. You can make a similar change in Firefox's Connection Settings.

---

### Post by GCR on 2006-08-26
Thanks for replying!

Well, my DSL network works with DHCP so everything is automatic(at least on Windows XP I dont have to add any DNS server a address and/or Router address). Also, I dont think I work behind a proxy for the same reasons(I dont have to add any proxy settings on WinXP, though I dont know if it is the same for 2.6.xx kernels)

Either way Illcontact my ISP to ask for the DNS web server addresses to see if theres finally a workaround for this.

---

### Post by GCR on 2006-08-26
Hey guys! Well my /etc/resolv.conf has this:

nameserver 192.168.0.1

is this how its suppossed to be? That is the IPo of my router I believe. My PC has 192.168.0.101

Is this right or is something wrong?

UPDATE: I can ping to 192.168.0.101(myself), 192.168.0.1(the router I think), 127.0.0.1(loopback) and 192.168.0.100(another computer on my network).

---

