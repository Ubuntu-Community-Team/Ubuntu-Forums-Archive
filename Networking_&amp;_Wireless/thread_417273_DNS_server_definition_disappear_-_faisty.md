---
title: "DNS server definition disappear - faisty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by orengabay on 2007-04-21
Hi all,
I use Faisty (but the problem also was in Dapper).

I have an open wireless network at home.

When I try to work without roaming I can't connect the wireless network. When I setup roaming - it is working but from time to time the network profile change and then I lost the DNS definitions. When this happen, I open the networking form,  reselect the HOME location, DNS server come back and I can continue to work.

I think that part of the problem is with my router that do not sent the DNS information from some reason but I was not able to fix that because the router is very old.

How can I set it so that the DNS settings will not change? 

Thanks,
Oren

---

### Post by spd106 on 2007-04-21
Edit a line in your /etc/dhcp3/dhclient.conf, where is say prepend domain name servers replace the localhost address with your gateway/router and uncomment the line.

---

### Post by orengabay on 2007-04-21
Thanks for your reply - I did that but after that the computer was not able to resolve any address.
I had to delete and select the HOME profile manually again.

---

### Post by orengabay on 2007-04-28
an update.
The problem was solved after I added a second saved location to the network profile. Am don't why but now I after I select the needed profile it is kept and I don't need to reselect every few minutes.
Thanks

---

