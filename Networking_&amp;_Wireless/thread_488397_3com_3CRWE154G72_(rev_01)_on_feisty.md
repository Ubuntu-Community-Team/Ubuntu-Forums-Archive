---
title: "3com 3CRWE154G72 (rev 01) on feisty"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by trondhuso on 2007-06-30
Hi there,

So I upgraded from 6.10 to 7.04 and then the 3com card 3crwe154g72 (v1) stopped working.
When I do lspci it comes up as 03:00.0 Network controller: 3Com Corporation 
but no lights or anything happens on the card. 

I've tried to put the isl3890 (1.0.4.3.ram-file) in the normal places for it without any luck. 
I've also read that there are problems with this card on feisty because it uses the prism54pci or prism54common firmware.

Has anyone else made this card work under feisty?

Best regards,
Trond

---

### Post by trondhuso on 2008-01-31
In Gutsy this card starts blinking and the network manager will pick it up. But it won't connect to any networks. 
Buggy Drivers?

This is run without NdisWrapper.

---

### Post by trondhuso on 2008-01-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176602](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176602) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				So I have read and re-read and even filled a bugreport, and then all of a sudden the solution is standing there in front of your (now) blood-squirted eyes:
Kill a dhclient for the wireless.

But there is a bug there. The card is called wlan0_rename which indicates that not all has gone like it should. 

By killing the dhclient and trying to connect again the connection worked. neat.

I have filed my information regarding the not connecting to Launchpad: 
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176602](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176602)
(hopefully it was posted to the correct thread)

Hope this helps someone.

best.

Trond

---

### Post by trondhuso on 2008-05-03
Just want to inform that the card is working perfectly under Ubuntu 7.10.

---

