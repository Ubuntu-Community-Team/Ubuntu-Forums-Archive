---
title: "Wired Internet through Wireless Router"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by tonyr1988 on 2006-10-10
I have a Linksys WRT54G wireless router. The laptop (that I'm on now) and my desktop both have Ubuntu Dapper on them. Since my desktop doesn't have a wireless card, and I'm cheap, this is the setup:

Laptop: Connected through router (wireless)
Desktop: Connected through router (wired)
Network printer: Connected through router (wired)

For some reason, my desktop won't connect to the Internet. It worked previously (before I had a router, when it was directly connected to the modem. My printer works perfectly.

I've changed the ethernet cords - it didn't work. I checked the DNS - same as my laptop. I've restarted a lot - no difference. Pinging any site (or trying to do a 192.168.1.1 to see my router's config) doesn't work. Switching the ethernet cord to slots 1, 2, 3, or 4 on the router doesn't work.

Any ideas on what I can do? I'm assuming Ubuntu detects my ethernet card fine - it used to work when it was directly connected.

Thanks,
Tony R.

PS Both the lights (orange and yellow) light up on my ethernet card.

---

### Post by mips on 2006-10-10
What does the output of the following commands say:

lspci -v
ifconfig -a
cat /etc/network/interfaces

---

### Post by tonyr1988 on 2006-10-10
I feel retarded....

I restarted the router and it's working again. :) 

It's weird, though - I had to restart it yesterday (wireless wasn't working), and my wired connection didn't work before or after the restart.

If it starts messing up again, I'll run those commands and post here.

Thanks!

---

