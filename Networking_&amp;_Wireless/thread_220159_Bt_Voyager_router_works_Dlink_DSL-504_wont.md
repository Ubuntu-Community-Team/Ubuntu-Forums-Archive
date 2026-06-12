---
title: "Bt Voyager router works Dlink DSL-504 wont"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by redo109 on 2006-07-21
Hi I have a couple of ADSL routers the oldest a BT Voyager 205 and my new one a Dlink DSL-504, I've set them both up the same and using XP both connect to my Tiscali braodband but, If I use or install the Ubuntu live CD I cannot connect to the internet with the Dlink, I can connect to the Dlink web admin page on 192.168.1.1 but cannot get onto the outside world. If I load the Kubuntu live CD I can connect and install and still connect just the same as XP. Yet the Dapper 6.06 live cd wont. I can ping the Dlink as you would expect because I can connect to it's web server. I don't want to lose any more hair has anyone any ideas
Thanks
Richard

---

### Post by coffeecat on 2006-07-21
If I read you correctly, the Kubuntu CD will connect to the internet through the D-Link router, but the Ubuntu one won't. Don't understand that but, whatever, I think it might be worth checking to see this isn't the IPv6 issue causing the problem. Windows XP isn't yet enabled for IPv6 (afaik), but most Linux distros are. Inadequate or old router firmware is confused by IPv6 modified IP addressing, and you get what you are experiencing.

In fact, this is what I experienced with my D-Link-G604T wireless router last year. Windows connected fine, but most parts of Linux didn't. Disabling IPv6 in whatever Linux distro I was using was a workaround until I updated the router firmware and then, bingo, everything was hunky-dory. :wink:

A quick experiment. Fire up Ubuntu with your D-Link connected and start firefox. Type 'about:config' in the address bar (without the quotes), and then 'ipv6' (again no quotes) in the filter. You should be seeing a line beginning 'network.dns.disableIPv6'. Double-click on 'false' (or right-click) and it will change to true. You have now disabled IPv6 in firefox. Close it down and start it up again, and if you can now browse the internet, IPv6 was your problem. If not, sorry - don't know what's going on.

If it is IPv6, search these forums for ways of disabling IPv6 globally in your installed Ubuntu or, much better, upgrade your firmware if it is available.

---

### Post by coffeecat on 2006-07-22
I've just realised how Kubuntu can connect to the internet when Ubuntu doesn't - if that is indeed what you are saying. *If* you are using **Konqueror** in Kubuntu to browse the internet and can do so, but with **Firefox** in Ubuntu you cannot, then this really is the IPv6 issue. Absolutely. 150% certain. Completely sure. No question. :D

Let us know how you get on.

---

