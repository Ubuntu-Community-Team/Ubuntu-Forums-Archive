---
title: "Network device disappeared"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by adammw on 2008-09-08
Hi.
I've been unable to get my Ubuntu server system (with a IceWM frontend) to connect to the network lately. It was working before, but alas, I did not create a backup (how stupid of me). Anyway, I need help to fix it. The network card is a PCnet-FAST III. I've tried to reboot (duh), ifup eth0, ifconfig eth0 up <ip-addr>, and lots of other things but it just ain't working. It's in a VirtualBox machine, but I don't think that is the problem as nothing has really changed, and I've checked that the adapter is enabled and the cable plugged in. I've also tried to disable and enable the adapter but no messages appear in the system log.
On startup, everthing goes [ OK ], but it's still happening.
I've also seen this in the messages log (don't know if it helps):
> pcnet32: PCnet/FAST III 79C973 at 0xc020, 08 00 27 2a 17 72
pcnet32: Found PHY 0022:561b at address 0.
eth0: registered as PCnet/FAST III 79C973
pcnet32: 1 cards_found but still not working.

Any help will be greatly appreciated.
Thanks...

---

