---
title: "No internet through PCMCIA modem"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by antonionunes on 2005-05-12
Hi,

Running Ubuntu Hoary on a Toshiba Portege. Internet works fine when connected through broadband/ethernet. However when connecting through a PCMCIA modem no such luck.

The modem appears to be recognised and to work. If I use Gnome PPP then the modem connects to the ISP but after the connection is established browsing the internet or sending and receiving emails doesn't work.

Trying to connect through the Network Settings control panel I can't get the modem to connect. When I activate the modem connection on the first tab, it will say the interface is activated, but the modem doesn't even seem to be accessed. I can also not get any modifications to any of the tabs to stick. There is a default gateway device which is eth0. ppp0 doesn't show up here. Not sure if that is important.

Just in case: The modem is a 3com Megahertz 56k Global Modem (3CCM156 B).

Oh, and the ISP for the modem connection is a different one from the ISP for the ethernet connection.

So the question is: has anybody any exprience with this set up and/or know how to fix the internet connection.

Kind regards,
António Nunes

---

### Post by antonionunes on 2005-05-13
OK. I can connect now, browse and email, but I can't make changes made in the Network Settings control panel to stick. I need to edit the modem connection every time to add username and password, and correct the modem port.

Can anybody tell me where the config files for this app are stored? Maybe I need to chmod it, or otherwise I could manually edit the file(s).

Kind regards,
Antonio

---

### Post by jkndrkn on 2005-05-30
Antonio, a question.

I originally had the same problem as you. My modem seems to dial out and connect but I can't browse or send/receive email. How were you able to get the modem connection to work?

Thank you.

---

