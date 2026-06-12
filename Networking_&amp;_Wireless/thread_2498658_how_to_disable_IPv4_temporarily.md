---
title: "how to disable IPv4 temporarily"
date: 2024-06-22
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2024-06-22
IPv6 is already working and seems to be preferred if the site has an AAAA record in DNS.  what i want to do is confirm a site by temporarily disabling IPv4 and trying to access it, again.  i only need to do this for Firefox but doing it system-wide is preferred so it will be in effect for everything like lynx, ping, telnet, traceroute, and so on.   i would like this to be a simple thing like an on-off switch, or a command (i always have a shell open).  i would prefer it works for a non-root sudo-restricted (cannot use root) user (which i am usually using).

i'd also like to know how apps like web browsers implement a preference.  do they just delay trying IPv4 if a DNS AAAA record comes back and end the delay if IPv6 quickly fails?

---

### Post by currentshaft on 2024-06-23
I don't think you want to disable IPv4 entirely since your IPv6 route is likely only outside your gateway. You still need IPv4 to connect locally.

What you probably want instead is something like dnsmasq or dnscrypt as your resolver to block A queries and only forward AAAA ones.

---

### Post by Skaperen on 2024-08-07
i really do want IPv4 traffic disabled.  but i do have a tunnel going over IPv4 to carry IPv6 traffic to reach the world.  so i think the solution is to create a dead interface that looks to be alive, default route all of IPv4 to it, and set up simple /30 routes for my existing IPv4 connection (wifi) and the far end of the tunnel.  then i need to find a way to get Linux to discard incoming IPv4 traffic not intended for these 8 addresses, as soon as possible, before it reaches regular filtering.  the tunnel does have an IPv4 interface on each end, but i can unconfigure that.  when i get another computer on my LAN i want it to be pure IPv6 operating as if IPv4 no longer exists or never did exist.

---

### Post by currentshaft on 2024-08-07
who

---

### Post by Skaperen on 2024-08-08
if IPv4 is working, something could be using IPv4, and the test result would be misleading.

---

### Post by Skaperen on 2024-08-08
"A dead interface that looks to be alive"

OK, i was not very clear.  an interface that appears to be functional but every packet sent is discarded.  this can be implemented in software, i'm sure.  my poor memory tells me that i've done this before.

---

### Post by Skaperen on 2024-08-08
> Then simply don't return ipv4 DNS records, which is how most if not all connections will originate, to the LAN clients. 				

i can't be sure everything always uses a host name.  there is such thing as connecting to a specified IP address, in both IPv4 and IPv6 (i doubt it happens as often in IPv6 but i have done that, before)

---

### Post by currentshaft on 2024-08-08
iv

---

### Post by The Cog on 2024-08-08
This one requires root, but should work for you. It makes the route unreachable, so your app won't just use IPv4 and declare a timeout, but will know there is no IPv4 route. Assuming the target is 192.0.2.77: **[FONT=Courier New]sudo ip rule add unreachable to 192.0.2.77[/FONT]**
Use **del** instead of **add** to remove the rule it again. You can use **[FONT=Courier New]ping 192.0.2.77[/FONT]** or **[FONT=Courier New]ip route get 192.0.2.77[/FONT]** to check the route.

P.S. You may need to add a priority to make sure your rule has a greater priority (lower number) than the VPN. Try a low-ish number like 100. You can see the current rules with **[FONT=Courier New]ip rule[/FONT]**. Add the priority like this: **[FONT=Courier New]sudo ip rule add unreachable to 192.0.2.77 priority 100[/FONT]**

---

### Post by Skaperen on 2024-09-06
i don't really understand this.  it seems to be blocking just one IPv4 address.  i want to block all of IPv4 except one to four addresses while leaving IPv6 wide open routed via on to four tunnel(s).

---

