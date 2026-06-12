---
title: "Sky router being reset (solved!)"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by skotl on 2007-12-13
Hi all,

this is a really weird one. I was running an IPCOP firewall for a looooooong time and only recently switched to Sky, who provide a Netgear DG834GT modem.
Everything is great, until I switched to my VMWare server, which is running on Ubuntu 7.04 Feisty Fawn.

All is good; start firefox and run a bunch of web queries / downloads, etc, etc.

But... Whenever I started Update Manager, or ran apt-get, the Sky Router would reset its WAN connection every 10 secs. To say this was annoying would be an understatement.
Even with other systems connected to the router, the connection was dropped within seconds and then taking up to a minute to recover.
To be clear; if I did *anything* in Ubuntu (web browsing, FTP download, etc) or on any other connection (external laptop, wireless, to the router) all was good. It was *only* Update Manager / apt-get that killed it.

Anyways, tonight I replaced the 10Mb/s 3Com Etherlink XL PCI network card with a generic Dell PCI card and everything is fab; no problems.
Moral of the tale is this; certain types of traffic (apt-get) over certain types of card (EtherLink XL) may cause certain types of DSL (Sky) to fail.

Skot..

---

