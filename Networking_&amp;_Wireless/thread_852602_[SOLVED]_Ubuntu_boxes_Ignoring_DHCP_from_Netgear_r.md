---
title: "[SOLVED] Ubuntu boxes Ignoring DHCP from Netgear router"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Grandma_DOG on 2008-07-07
I started having trouble on a Netgear NAT router.  The router worked fine  for over a year.  I run a data warehousing server group and use a Netgear router to reserve IPs on a DHCP network. The Netgear router is the DHCP server. We need these machine IPs to stay static without creating static IPs for each frilling box.

So 2 weeks ago, after a long time, we rebooted a couple of boxes.  We noticed they didn't take their reserved IPs, but took IPs outside of the range ie. range was x.x.x.100 and they took x.x.x.150.  Things we did different was we upgraded some ubutu boxes from Dapper to Fawn a few months ago.  I also thought one box on the network might have DHCP server accidentally on and interfearing, but I couldn't find anything.

So I thought the old Netgear router was crapping out and ordered 2 new Netgear routers, one for production and one for back up.  Guess what?  The new routers show the same weird stuff, Ubuntu boxes are not taking the reserved IPs they are supposed to.  Looking at 
>sudo dhcpclient eth0
 they seem to be requesting "DHCPREQUEST" the goofy IPs.

Any ideas on the cause or the fix?

---

### Post by The incredible bulk on 2008-07-07
First suggestion: Lose Netgear!!

Now that I've got that off my chest....

Tell me about the your netgear assigns the Static DHCP maps. Do you put in the mac or does it pull it by name of some sort? A model number might answer that question for me.

TIB

---

### Post by lisati on 2008-07-07
> **The incredible bulk said:**
> First suggestion: Lose Netgear!!

Now that I've got that off my chest....

Tell me about the your netgear assigns the Static DHCP maps. Do you put in the mac or does it pull it by name of some sort? A model number might answer that question for me.

TIB
Ditto with the unexplained behaviour noted by the OP

I think my netgear gizmo associates by MAC address... most of the time the Netgear beast & the PC get the static IP address right according to how I think I've set it, occasionally it doesn't. I haven't figured out a pattern yet......

---

### Post by Grandma_DOG on 2008-07-07
> **The incredible bulk said:**
> First suggestion: Lose Netgear!!

Now that I've got that off my chest....

Tell me about the your netgear assigns the Static DHCP maps. Do you put in the mac or does it pull it by name of some sort? A model number might answer that question for me.

TIB

I'll may post them when I get back up to work.  But does it matter if 2 different Netgear models are showing the same symptom?

---

### Post by Grandma_DOG on 2008-07-13
after several days of frustration, i finally solved the mystery.  in fact, i predicted it in the first post.

It was a interfering NAT router with DHCP still on that had been plugged into the network to replace a failed hub.

---

