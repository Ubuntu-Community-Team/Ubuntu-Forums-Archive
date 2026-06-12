---
title: "Network Topology Advice"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by kafkaian on 2007-11-05
Hi people, I am looking for some general advice on setting up a LAN at home. I have 3 PCs, 2 recent Intel dual core  and 1 older P4 at my disposal. The dual cores are currently set up as Ubuntu stand alones fed into an old netgear wired router and firewall coming off a cable modem

I'd like a common NFS such that people can hot desk the satellite PCs (and eventually a wireless laptop and PDA)

So I'm thinking, get a linksys/netgear/d-link router/hardware firewall and hard wire the P4 as NFS, one of the dual cores as hard wired leaving the remaining dual core as wireless given that it has onboard WiFi. 

I would also like the NFS to serve music to a system at some stage either via an independent audio box or simply loading a package onto the NFS P4.

Am I going about this the right way? Could the P4 also be used to route the other PCs thus dispensing with the independent hardware router? Or should I use one of the faster dual cores (Intel 3GHz) as NFS?

Any general guidelines would be helpful, or please just kick me into the right ball park.

The idea of the NFS is to simplify (and guarantee) backups and getting everyone working from the same hymn sheet. I have important files floating everywhere at the moment and have to be mindful of several backups, whilst file duplications are an issue

many thanks

Ian

---

### Post by kafkaian on 2007-11-05
Any other threads people know of where this sort of thing has been discussed?

---

### Post by kafkaian on 2007-11-05
This site is giving me a good grounding of some of the principle thus far:

[Linux Home Networking]("http://www.linuxhomenetworking.com/")

---

### Post by tkharris on 2007-11-05
I would highly discourage what you're doing.  Having three+ computers using an NFS mount from another server will lead you to having a lot of iowait issues, slow performance and general evil.  Instead use the other server as either an svn server, and make everyone checkout/checkin when they use a computer or have a backup and consolidation policy.

---

### Post by kafkaian on 2007-11-05
Thanks for the advice. I clearly need to give it more thought, but I was under the impression that this was exactly what NFS was for?

---

