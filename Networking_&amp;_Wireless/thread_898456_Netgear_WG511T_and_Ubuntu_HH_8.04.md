---
title: "Netgear WG511T and Ubuntu HH 8.04"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by whittycat on 2008-08-23
I have recently installed Hardy Heron on a laptop and I have a Netgear WG511T cardbus wireless adapter. I don't know the version but the chip is AR5212/AR5213. I am using the Madwifi driver built in to 8.04. It works well (mostly; just a minute ago it lost the connection for no reason) if I am close to the router, viz about 1.5m but if I move to the room next door, about 7m from the router, I cannot get it to work at all. All the configurations are  correct and Kwifi manager says that there is a connection but dhclient won't deliver an IP address. At times I can get an IP address but if I ping the router I get 'Network unreachable'. The link signal is about 24/70. I really want it to work on the top floor of the house but there's obviously little hope of that even though I have in the past run a Prism2 USB adapter up there perfectly well. Some posts in this forum suggested that I might be getting interference so I switched from channel 6 to channel 11 (my neighbours are on channels 1,1 and 7) but that made no difference. Other posts say what an excellent adapter the WG511T is. What can I do to find out what the cause of the problem is? Should I move to a USB adapter? SuSE? Fedora?

---

### Post by whittycat on 2008-08-25
A bit more information. I have another laptop with built-in Intel 2200BG wireless and Ubuntu HH and this works very well. I took it up the garden (22m) and it still works, with link quality 53/100. So is the cardbus adapter faulty? I don't think so; it happens I have a spare and this behaves the same way, ie it will connect only if really close to the router. Something wrong with the laptop I was using with the Netgear WG511T? Well, I installed linux-restricted-modules on the other laptop so that I could run the cardbus adapter as well as the Intel 2200BG and guess what? Hopeless. Link Quality 7/70 and can't connect at all. It's an Atheros chipset so the ath-pci driver is the right one and I have a Netgear router too. So why do other posts in this forum say that the Netgear card is the best in the world? Not in my house it isn't. Reviews of this card say that you should have a good signal at 69m.  What do you think?

---

### Post by glibik on 2008-09-09
A local computer shop has a Netgear WG511T on sale for $AU29.  Was thinking to buy it for my Ubuntu 8.04 Dell laptop, but decided to check this forum to see what sort of support there is for it.  

Haven't yet seen other posts that say "the Netgear card is the best in the world". So am now thinking I'll let this sale go by. :-\

If it's any consolation/help, I have a Netgear WG111v2 that works fine. :-) 

P.S.  Apparently the "v2" part is important. :-\

---

