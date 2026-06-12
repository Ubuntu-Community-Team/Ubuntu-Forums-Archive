---
title: "name resolution question"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by chris_tikva on 2008-10-10
Sorry if this is a naive question but I've looked for an answer and can't find one.

I have a LAN connected to a router and thence to the internet. The router provides a DHCP service and if I look at the list all the computer names are there together with their assigned IP addresses.  Also if I look for "network places" from any of the individual machines they can all be found and each machine seems to be able to know the names of the others.

However, if I ping any of the machines I can only get a response by pinging the IP address, not the host name. Same with ssh. How can I get ssh to recognise the name of the computer I want to log into?

Thanks,

Chris

---

### Post by yogensha on 2008-10-10
The 'network places' stuff uses Samba's nmbd service to resolve names.  This is distinct from the rest of the system, which uses the normal system resolver.  AFAIK, the two don't talk.

The easiest way to get your machines to ping or ssh each other by name is to adjust your /etc/hosts file.  You can add an entry for each machine you want to reach by name.

If you have more than a couple of machines, this can be a huge hassle, and you'd need to look at running a full blown DNS server on your network.

---

### Post by lavinog on 2008-10-15
does nmblookup resolve the correct ip address?

can you output your /etc/nsswitch.conf?
somewhere on the hosts line you should see wins, if not add it:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins

```

---

### Post by Iowan on 2008-10-15
> **yogensha said:**
> If you have more than a couple of machines, this can be a huge hassle, and you'd need to look at running a full blown DNS server on your network. **dnsmasq** is less than full-blown DNS server, but can (reportedly) tie DHCP and DNS together.  I have it on my Freesco router, but I'm not using it.  Sometime soon, I may move DNS from router to services box and install **dnsmasq** there.

---

