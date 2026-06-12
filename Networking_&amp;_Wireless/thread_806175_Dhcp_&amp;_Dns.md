---
title: "Dhcp &amp; Dns"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by panth13 on 2008-05-24
All,
 I'm trying to set up my ubuntu distro as my home network's DHCP & DNS server. However I'm running into a small problem.

I use both my ethernet card & my wireless NIC to connect to my network depending on where I am. I would like to be able to keep my host name the same, regardless of which means I am using to connect.

Does anyone know how to configure the DHCP server to assign a host name to either of two different IP addresses?

And how to make a DNS server support resolution to either one given the host name?

Is this even possible or have i gone off the deep end? Any help would be appreciated. Thanks!

-B

---

### Post by lisati on 2008-05-24
In theory it's possible. I have a router which allows both wired connections and wireless connections - when I've hooked up my laptop via a wired connection the router assigns one address to the wired connection, and another to the wireless connection. Possibly part of the answer is to get it to recognize the different MAC addresses of the adapters but I'm not sure of the details of the "how to"

---

### Post by panth13 on 2008-05-24
Right, same with my other router. What i'm really trying to accomplish is that whether i connect using my wireless or my wired NIC, when i tell another computer to connect to my laptop, i don't have to specify a different hostname. I can always use the same name.

-B

---

