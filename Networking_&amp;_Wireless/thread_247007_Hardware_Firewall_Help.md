---
title: "Hardware Firewall Help"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by Probus on 2006-08-30
I am a total newbie to Linux, so please excuse the very basic nature of these questions.

I am attempting to set up a hardware Linux firewall using an old PC, to protect my company laptop which is running Windows. Although I would also like to give my other computer (a desktop running Dapper Drake) the extra protection of a firewall at certain times, I will never be running these machines simultaneously, so it is a really just a basic 'network' of one. I will just swap the ethernet cable from one machine to another as necessary.

I am hoping to use either Smoothwall Express or IPcop on the firewall machine. My main problem is understanding exactly how the computers are wired together and how many network cards I need. I use a wireless router to connect to the inter-net (broadband account). It is a Linksys wireless-G ADSL Gateway (model WAG54 GS), but the wireless part of this is never used and I just hook up the laptop to this using the supplied cables. 

1) My understanding of the wiring is as follows: 
wall socket, then Linksys router, then straight through ether-net cable with RJ 45s at each end connecting to the firewall computer, (all on the red network), followed by a twisted pair ether-net cable to the protected laptop, (green network). Is this all correct so far?

2) My firewall computer only has one RJ45 socket. If I use the above setup, it appears that the firewall computer will need two network cards (ethernet?), one to take one RJ45 connector from the router side and another to take the other RJ45 connecting cable to the laptop. In the motherboard specifications on the firewall machine, it shows a ''LAN Speed: 802.3u (10/100 Ethernet), supports Wake-On-Lan''. Do I need to get two totally new network cards or can I use the one on the motherboard as well? Any suggestions on good 'Linux friendly' network cards would be appreciated. 

Any other recommendations on setting this up would be gratefully received!

Thank you in anticipation of your help.

---

### Post by Original Brownster on 2006-08-30
Hi,

> 1) My understanding of the wiring is as follows:
wall socket, then Linksys router, then straight through ether-net cable with RJ 45s at each end connecting to the firewall computer, (all on the red network), followed by a twisted pair ether-net cable to the protected laptop, (green network). Is this all correct so far?

Yes, the final cable computer to laptop will need to be a crossover cable.

> 2) My firewall computer only has one RJ45 socket. If I use the above setup, it appears that the firewall computer will need two network cards (ethernet?), one to take one RJ45 connector from the router side and another to take the other RJ45 connecting cable to the laptop. In the motherboard specifications on the firewall machine, it shows a ''LAN Speed: 802.3u (10/100 Ethernet), supports Wake-On-Lan''. Do I need to get two totally new network cards or can I use the one on the motherboard as well? Any suggestions on good 'Linux friendly' network cards would be appreciated.


Without knowing the chipset for the one on-board it's hard to say, generally though, most nics are supported, possibly the easiest way is to run the installer for the firewall and see if it recognises an ethernet card, if it does your good to go and just buy one, otherwise buy two, they are so cheap these days.
As to which to buy, I shop at ebuyer.com, some say linux / unix compatible.

Check out this [link]("http://www.tldp.org/HOWTO/Hardware-HOWTO/nic.html") for supported adapters.

---

### Post by Probus on 2006-08-30
Hi Wayne,

Thank you very much for the very speedy and informative reply. To save complication I think I will go for the two card option. Cheers once again for the much needed help.

Regards,

Probus

---

