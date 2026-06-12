---
title: "My gateway server as DNS server"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by xeo_pt on 2008-07-26
I have a server that acts as a gateway to the internet, but
in the clients computer I have to tell the real DNS servers.
I know that I can put in the DNS servers the same IP as the gateway.
How can I do that?

Thanks ins advance.

---

### Post by SpaceTeddy on 2008-07-27
three possible solutions i see here:

1.) use a dhcp server that issues the "outside" dns to the clients as well as their ip configuration

2.) use dnsmasq. This will turn *not* turn your computer into a dns server, but will make it possible for computers on internal network to query your gateway for dns. Meaning, your router will NOT acctually answer the queries, but will forward them to the external dns server. The beauty is that it "looks" like you have an internal dns server, but in reality, the gateway is only forwarding.

3.) use bind. This is a full DNS server. A bit of a bitch to setup and understand at the start, but bind can do anything you possibly want from a dns. This *is* a full dns server.

I personally would use a mix between 1 and 2. I would use the dhcp, but not issue the external dns servers but the gateway itself which runs dnsmasq. Easiest to setup - and simple to maintain with little overhead.

hope it helps :)

---

### Post by xeo_pt on 2008-07-27
Thanks a lot!
Thats it.:guitar:

---

