---
title: "Network Setup Ideas..."
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by prodezigner on 2007-11-27
Alright, I'm designing a budget home file server (SSH + SAMBA + rTorrent), the board I'm getting is the gPOS one from ClubIT (60 bucks, can't beat it w/ LAN, Video, CPU and low power consumption). I've read it's mATX and Nano-ITX (thinking it's mATX though).

It's got onboard LAN... check.
Two PCI slots... check.

What would be the best way to network this? Get two NIC cards for the PCI slots, bond them for rTorrent and dedicate the onboard for SAMBA, or just one NIC for SAMBA and rTorrent? Or one and one? I know download speed is limited by ISP, but I really don't know the advantages of teaming vs. non-teaming.

ALSO... how in the world do you use those RJ45 wallplates? How would you run CAT5 in your wall w/o totally demolishing or having to repair the wall?

---

### Post by prodezigner on 2007-11-27
I'm adding to this post instead of editing for two reasons, to better address my situation and to bump it.

My internet is going to be throttled (32kbs up / 128kbs down) for the most part, when I'm not at home it's going to be non-throttled (rTorrent power!) while I'm at college or when everyone is asleep...

So that's a better idea... my connection is a 6Mbs Down 256Kbs Up cable connection...

---

### Post by IamAcoconut on 2007-11-27
I don't quite understand what you mean about the network cards...
If you want this PC to not only act as a file server, but enable access to files between the PCs connected to it, then I think you should use a switch, or it won't work.
Please excuse me, if I'm being ignorant.

---

### Post by prodezigner on 2007-11-27
Here's my current LAN setup...

Cable Modem -> Wireless Router -> Network Hub -> Network Hub

The router has one computer hard wired... and another wire running to  one of the 5-port hubs. The wireless router also powers two laptops, one desktop and a Wii.

The hubs have two nics from my gaming rig hooked up, an ethernet printer, a nic connection from my fiance, and one running to the server currently.

When I download it locks up the internet and I'm thinking I'm going to have to replace the hubs with a switch... any suggestions on which one?

But what I'm asking, would two NICS help in bandwidth, speed? I guess what I'm asking... what's the best way to setup a home network with what I'm attempting to do... (headless torrent server that serves to *ANY* computer on my network without passwords or accounts.)

---

### Post by Whiffle on 2007-11-27
what kind of router, some of them don't handle torrents very well.

---

### Post by prodezigner on 2007-11-27
Router = Linksys WRT54GS
Hubs = 5-Port Linksys x 2

---

