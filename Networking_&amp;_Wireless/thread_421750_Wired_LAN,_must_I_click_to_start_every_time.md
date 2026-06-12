---
title: "Wired LAN, must I click to start every time?"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by kdnewton on 2007-04-24
Hi all. I've been puzzling over this for a few days now. Back in every previous version of Ubuntu I could just install when connected to my LAN and Ubuntu sees that I'm connected to the net and sets that up for me automatically every time the computer turns on.

However, since I've done a fresh install of Feisty Fawn this is what happens. I turn on the PC. Before I have logged in I try to SSH from another computer to this feisty fawn. No route to the feisty fawn. So now I log in to feisty fawn and try to bring up a web page, or ssh out to another computer on the network. The LAN icon, when I hover over it, that there is no wired network connection. Keep in mind, I have *only one* network card in here.

lspci give me
00:0d.0 Ethernet controller: Winbond Electronics Corp W89C940

So no network connection until I manually left click the LAN icon and select "Wired Connection" at which time the feisty fawn makes a connection and I can now finally make inbound and outbound connections.

I've tried setting it to "Enable roaming" and that didn't work automatically either. It's set to automatically accept DHCP. So far no luck on my part.

Please, how can I have the PC automatically make a network connection every time the PC turns on, before I've even logged in? Hopefully with things not set statically as I do have my computers lease addresses through my router.

---

### Post by musicinmybrain on 2007-04-24
Same problem here. Any answers on this? It's no showstopper, but it's mildly annoying to have to manually select my wired network at every boot.

---

### Post by musicinmybrain on 2007-04-28
[Bug #97278]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/97278") covers this issue. Some have suggested it's a duplicate of [Bug #83143]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/83143").

No known solutions yet, though.

---

