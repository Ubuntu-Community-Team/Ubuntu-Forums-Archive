---
title: "IPv6 with wireless"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by kritzstapf on 2008-04-07
Hi :)

I am setting up IPv6 addresses in my local network these days. Im using a machine running radvd to advertise the subnet to the clients. Using cabled network everything works fine, i get an ip address and i am able to use ip6.
Using my wireless interface just sets a tentative link local address and nothing more happens. Ive done some debugging with Wireshark and found out that my cabled interface send an router solicitation which the wireless interface doesnt, wireless just does neighbor solicitation.

How do i set my wireless do send router solicitations so i get an ip address from radvd?

Or am i missing something else?

Greetings,
Christoph

---

### Post by kritzstapf on 2008-04-09
i was using the iwl3945 driver which seems to have serious problems with inet6. after switching back to ipw3945 it works fine

---

