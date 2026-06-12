---
title: "Slow network response times when using Motorola WR850G Wireless Router"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by monocongo on 2007-02-20
I have recently installed Ubuntu and I have noticed that my connection to the Internet is now quite slow, sometimes taking as long as 10 seconds to get to common sites such as Google, etc.  I have determined that the trouble is with my wireless router, a Motorola WR850G, which is between my desktop system and my cable modem (there is a second laptop in the house which requires wireless access -- the Ubuntu desktop system is wired).  When I bypass the router and plug directly into the cable modem I have quick response times, almost never waiting longer than a couple of seconds for any page, and usually no wait for pages at all.  I didn't notice this slowness of response before when I was using Windows XP on this desktop, so I'm assuming that this is a result of the Ubuntu installation.  Is this possible, or am I mistaken and just more sensitive to this now that I'm paying closer attention for any problems with my Ubuntu configuration?  If so then what can I do to reduce the response time when I'm plugged into this wireless router?  Is it possible that there needs to be a modification to the router's configuration instead of monkeying with my Linux network settings?

Thanks in advance for any suggestions.


--James

---

### Post by gradedcheese on 2007-02-20
Some routers are very bad with IPv6, so you might want to disable IPv6 in ubuntu and see if that helps (search the forum for instructions).

---

### Post by monocongo on 2007-02-22
Thanks for the tip, disabling IPv6 seems to have made a difference.

--James

---

