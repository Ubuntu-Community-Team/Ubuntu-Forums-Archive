---
title: "Wireless and internet! Problem with hosts or dns?!"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by VaDor on 2007-02-08
hi all,

I have a acer aspire 2200 with a intel 2200bg wireless network card into it. I proper configured the card with iwconfig and then I did a dhclient eth1 (eth1 is the wireless card).

I get ip  and i can enter with firefox in my router (192.168.1.1)  BUT I can't go to internet.. for example google.com or something..

Then in shell I  ping google.com and I obtain answers!!  So I tried apt-get update and one more time no connections.. he tries to connect but it can't!!!



I can ping external ip's/dns  and I can enter in internal ip's!


What can be the problem???

---

### Post by VaDor on 2007-02-08
I solved the problem!!

This problem may be consistent with people that use routers.. I don't know why this is happen with ubuntu because previous versions (meaning 5.x) never had this problem!

Ubuntu puts the dns of the router  normally the router ip! So you can't resolve names.. e.g in firefox [www.google.com](www.google.com) don't work but if you put google ip you can access.

To resolve this situation go to your router admin page in status see the DNS of your provider(ISP), add to the list of your dns in networks and remove the router Dns from the list!

Problem solved

---

