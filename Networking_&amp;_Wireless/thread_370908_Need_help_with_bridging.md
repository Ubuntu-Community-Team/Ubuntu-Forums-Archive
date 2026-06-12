---
title: "Need help with bridging"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by qb4ever on 2007-02-26
Our pesky cat has chewed through the Ethernet cable running down stairs to the router for the last time.  I need to figure out a way to cut out the cable and still have access to the wireless capable router.

I have a spare box setup with an Ethernet card and a wireless card, what I'm trying to do is get the spare computer to pass packets from the router across the wireless card to the wired network and back transparently . I guess it's called "network bridging"



from internet: [internet] > [router] > [computer with wireless and Ethernet] > [wired network] > [wired computer]

to internet: [wired computer] > [wired network] > [computer with wireless card and Ethernet] > [router] > [internet]

How would I set this up under ubuntu?

---

### Post by solar george on 2007-02-26
Try installing firestarter firewall - it can configure connection sharing. (called Network Address Translation (NAT))

---

