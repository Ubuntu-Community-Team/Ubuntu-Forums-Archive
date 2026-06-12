---
title: "General Network problems"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by Stephen_at on 2006-10-25
After I finally got ubuntu installed (I had a pressed CD which checked out OK but would never complete installation - once I copied it and used the copy it all installed fine) I found I had problems with my network connections.

I have a linux server running dnsmasq and a Dlink Wireless router.

If I plug in using ethernet then I get an IP address from the server. However DNS servers are not set automatically (Even though dnsmasq is configured to send them). 

If I go to my wireless card (an old Belkin) then the configuration utility seems to know my SSID but no matter what I do I cannot get it to issue an IP address.

So any suggestions?

Steve

---

### Post by Stephen_at on 2006-10-25
If I do a iwlist scan I can see my network and my neighbours.

I've edited the interfaces file and put my encryption key in there but Ubuntu doesn't want to know -it jusr sits there claiming that no DHCP servers are responding

Its not much better on the ethernet card - sure I get an IP address from my DHCP server but I get NO DNS and I have to manually tell it what the gateway IP is.

Can't say I'm impressed - if Ubuntu is supposed to be bringing Linux desktop to the masses then its got a long long way to go!

---

### Post by Stephen_at on 2006-10-25
OK I'm making progress. I've had to change the wireless authentication to "both" on the router before Ubuntu would actually get an IP address.

---

