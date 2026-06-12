---
title: "Moved into new apt. with 802.1X configuration"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by DevilInPgh on 2007-09-14
I just moved into new university-owned housing that is connected to the broader LAN for the school.  The network configuration they use for their wired connections is 802.1X (yeah, apparently it's not just for wireless).  The IT guy was clueless as to how to connect my Ubuntu box to the network.  Does anyone have an idea as to how to do this?

---

### Post by rivalarrival on 2007-09-14
You're thinking 802.11b/g for wireless. If I'm not mistaken, 802.1X is basically standard 10/100 ethernet. 

If you're connecting to a typical lan, you PROBABLY need to set your network card to get a DHCP address.

system > administration > network 

select your ethernet card, hit properties

next to configuration, select "Automatic configuration (DHCP)"

Hit OK to close the window and it should get the proper settings from the network. (You did plug the computer into the school's network port, right?)

If that doesn't work, ask the IT guy for instructions for a Windows box and post them. I'm sure SOMEONE here can translate Windoze instructions into Ubuntu. :)

---

