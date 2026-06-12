---
title: "Homenetwork - WLAN and speed"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by Saubazi on 2006-08-20
I have two computers at home - one running with Ubuntu and a Media-PC running Gentoo in the living room. The living room PC has 54Mbps netgear adapter WG311 and this one has Netgear WG311T (108 Mbps).

I am not sure what to expect from the transfer speed but when I copy some files from one machine to another I reach only some 300 kb/s now that I am testing again some 1MB/s - is this normal or should there be a bit more power there?

What can I do to check that everything is as it should be?

Is the router somehow slowing the internal traffic?

---

### Post by funchords on 2006-08-20
1 MB/s is 8 Mb/s, which seems normal.

[How fast can I actually download over a wireless network?]("http://www.dslreports.com/faq/13587")

You have a two-hop wireless connection between the machines.  The first hop is from the local machine to the AP, the second hop is from the AP to the destination machine.

From that article...

54 mbps * one third = 18 mbps
18 mbps divided by two hops = 9 mbps

---

### Post by funchords on 2006-08-20
> **Saubazi said:**
>  some 300 kb/s ... some 1MB/s 

Variations like could be due to others on the same or nearby channels such as yours.  

Use 'iwlist scanning' to identify your neighbor's networks.  Select a channel at least 5 channels apart from theirs.

You might also have interference from 'hidden' networks and non-wifi products (phones, security cameras, baby monitors, etc.) that also use the 2.4 GHz band.

---

### Post by Saubazi on 2006-08-20
iwlist scanning shows no other devices than mine...
Would there be a way to use direct link between the two machines?
1 Mb/s was the absolute record and it was only today for the first time
that I had it, normally it is slower. Yet, this seems still to be below the expected so is there anything I can do?

---

### Post by funchords on 2006-08-23
You could try an adhoc connection, but unless you got creative with the topology, you would likely lose your Internet connection to those machines.

And, not all drivers support ad-hoc connections at speeds greater than 11 Mbps (a neat little exception carved into the 11g spec). :(

---

