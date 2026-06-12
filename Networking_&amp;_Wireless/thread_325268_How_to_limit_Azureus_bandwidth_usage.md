---
title: "How to limit Azureus bandwidth usage?"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2006-12-25
In our family we share the Internet through a router.  I use Linux and my sister uses Windows XP and she always clogs the bandwidth when she uses Azureus.  When she does I can't even do simple stuff such as browsing the Internet let alone play Battlefield 2 or World of Warcraft [-( 
Is there a simple click-and-point program that can assign to each user in the family network how much download/upload bandwidth they can use at a maximum?  Home networking has become unfair at our house.

---

### Post by ubernoob on 2006-12-25
You can limit the bandwith used in azureus itself. That will help alot. But it will still make your wow, bf connection suffer.

 If you have a DSL router, it might be possible to use QoS to make the bittorent traffic low priority. But that depends on the router. And there are usually not a gui for that. You have to read the manual and telnet to the router and set it up from there.

---

### Post by jingo811 on 2006-12-26
Seems like my Netgear router [http://kbserver.netgear.com/products/FM114P.asp](http://kbserver.netgear.com/products/FM114P.asp)
doesn't have QoS acording to this page:
[http://kbserver.netgear.com/inquira/default.asp?ui_mode=answer&prior_transaction_id=1502625&action_code=5&highlight_info=16777275,9,12&turl=http%3A%2F%2Fkbserver.netgear.com%2Fkb_web_files%2FN101482.asp&answer_id=17845083#__highlight](http://kbserver.netgear.com/inquira/default.asp?ui_mode=answer&prior_transaction_id=1502625&action_code=5&highlight_info=16777275,9,12&turl=http%3A%2F%2Fkbserver.netgear.com%2Fkb_web_files%2FN101482.asp&answer_id=17845083#__highlight)

I couldn't even find anything that says QoS when doing the 192.168.0.1 trick.
Anymore easy solutions?

---

### Post by ubernoob on 2006-12-27
then i would set up your sisters azureus to not take all the bandwith. There are probably some windows applications that can do similar stuff. But i'm not sure what to use.

---

### Post by jingo811 on 2006-12-27
Tnx I'll open up a can of whoopass it's probably the most simple solution to the problem.
> There are probably some windows applications that can do similar stuff. But i'm not sure what to use.
Nah, I'm scared of using Windows for things other than hardcore gaming.  Tnx for the tip!
Next time I invest in routers I'll make sure to buy some with QoS in them.

---

### Post by d3v1ant_0n3 on 2006-12-27
For windows (and linux, via wine) I'd recommend UTorrent over Azureus- it has a much lower memory footprint, and seems to manage bandwidth much better.

---

