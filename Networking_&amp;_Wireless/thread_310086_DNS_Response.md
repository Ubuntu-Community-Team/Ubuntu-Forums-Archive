---
title: "DNS Response"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by maclaxguy on 2006-11-30
Hey all,
I'm working on setting up a local DNS server, and so far everything is going great.  All the computers in my network are playing nice with it, except for my Ubuntu laptop.  When using it, I am not getting any addresses to resolve.

If I do, say, "dig digg.com" ( ;) ), I get this as a response:
```
;; reply from unexpected source: 192.168.1.105#53, expected 192.168.1.1#53

;; reply from unexpected source: 192.168.1.105#53, expected 192.168.1.1#53

;; reply from unexpected source: 192.168.1.105#53, expected 192.168.1.1#53
```


I opened up a sniffer, and I see the query being made, as well as my DNS server responding with the correct address.

If I change /etc/resolve.conf to the nameserver address (as opposed to the router address it was assigned), it works perfectly, but obviously with DHCP and different networks, this is unacceptable.

What gives?

Thanks for any help!

---

### Post by Tilex on 2006-12-01
It looks like you get an answer from another computer on the network instead of the gateway (your router)...I've no suggestion.

---

### Post by diepruis on 2006-12-01
Maybe there's a DNS running on 192.168.1.105?

---

### Post by maclaxguy on 2006-12-01
Yea, I guess i didn't make that too clear...
192.168.1.1 is my router, and 192.168.1.105 is my DNS server.  I set the DNS server on the router's config page to be 192.168.1.105.

---

### Post by diepruis on 2006-12-01
You can actually change the behaviour of DHCP to account for this.

Just add the following line to the start of /etc/dhcp3/dhclient.conf:
prepend domain-name-servers 192.168.1.105;

Now, after running dhclient, your resolv.conf will read:

nameserver 192.168.1.105
nameserver 192.168.1.1

---

### Post by maclaxguy on 2006-12-01
Ok, I'll try that out.  Any reason why all the others are working fine (3 MacOSX, 3 Windows, and the Ubuntu server), while this one laptop doesn't like it?

Thanks!

---

### Post by diepruis on 2006-12-02
My guess would be that the server, running a DNS is automagically configured. As for Mac OSX and Windows, perhaps they just don't report the "error"? I wouldn't know, since I've never used these tools on either operating system.

---

