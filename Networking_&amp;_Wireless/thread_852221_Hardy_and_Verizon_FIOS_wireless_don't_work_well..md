---
title: "Hardy and Verizon FIOS wireless don't work well."
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Rob Campbell on 2008-07-07
Hi,

I have a weird problem that occurs when I make wireless connections from my Macbook Pro and desktop (running hardy) to my Verizon FIOS wireless router. When I run bittorrent clients from these machines I loose wireless connectivity after around 10 minutes. 
- This doesn't happen from the machines using different OSes. So it's a hardy problem. 
- When the connection is down from one machine I can still access the network from another (so the router isn't crashing). 
- When I run a bittorrent client on the Macbook Pro on a different wireless router (that at work) it doesn't bring down the wireless. So it's not due to hardy alone. It's hardy + FIOS router.

Note that I'm not using WEP on the FIOS router because the Hardy machines wouldn't connect to it. The router does have MAC address authentication enabled. 

Anyone experienced anything like this or have ideas as to what I should tweak to get things working properly?

Cheers!

Edit: looks like the wireless does also go down with the router at work but it takes a lot longer.

---

### Post by Neobuntu on 2008-07-08
I can only say that I had issue with a Sprint EVO connection (Mobile PCMCIA CARD). While that is a different network, I had a very similar problem with KPPP (recommended) dropping the line after a few minutes. Auto redialing was not a clean solution. I **did** find a tweak to fix the "line" drop after much searching. I'm sorry I do not have a link to it. Don't give up. I think the same fix could solve your problem, as well.

It worked great after the fix but I did have a minor problem with Firefox needing to be switched from "Work Offline"; off it's "File" menu. Hopefully that problem has been upgraded.

---

### Post by Photogopher on 2008-07-14
I don't mean to pile on here but I too cannot connect to my VIOS wireless router using the correct WEP.  My card sees the router and shows good signal strength but it seems that the router doesn't like the Ubuntu/wireless NIC combination.  Verizon seems bent on supporting only Windows and not Macs or Linux machines.
Does anyone have some fix for this problem?

---

### Post by Rob Campbell on 2008-07-14
Yeah, I had this problem too and switched off the WEP. 

The deal with the connection dropping is probably an over-flowing NAT table or something along those lines. But it's probably at the Ubuntu end rather than the router end. I still get the problem at work but it takes longer because the connection is slower than my FIOS. 

Anyone have any clues as to where I should be looking on my Ubuntu box to fix this issue? I get it on the desktop and laptop. So far Hardy has been quite a pain...

---

