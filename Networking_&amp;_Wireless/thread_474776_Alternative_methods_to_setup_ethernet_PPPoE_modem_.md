---
title: "Alternative methods to setup ethernet PPPoE modem connection?"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by jasontan6 on 2007-06-15
I use a router which auto-connects to my ISP, so that isn't a problem when I switch between Windows and Ubuntu. Recently I had a friend who stepped up to try Ubuntu, and he uses an ethernet PPPoE ADSL modem to connect. I told him to goto:
```
System > Adminstration > Network
```
and setup a Modem Connection, but when I took a look myself, I realised it was for old dial-up modems.

I told him to wait for my phone call, so that I can search the Wiki for some answers. Luckily I stumbled upon this: [https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")

In a few minutes he was online. I searched thru the forums a few times, and it seems that nobody has asked this question before.

[LIST=1]
[*]Is there a GUI method to setup a PPPoE connection using an ethernet modem?
If yes, where is it?
[*]If no, why isn't it there?
[/LIST]

---

### Post by xthaparian on 2007-06-15
In Gnome there is PPoE software which you can use to get to PPOe

Go to synaptic and search for Ppoe. Then install it and....ban you are ready to go

Also check this out

[http://www.ubuntux.org/how-to-install-broadband-adsl-pppoe-client-rp-pppoe](http://www.ubuntux.org/how-to-install-broadband-adsl-pppoe-client-rp-pppoe)

---

### Post by jasontan6 on 2007-06-16
Found it, thanks xthaparian.

A little surprised why the Ubuntu team decided not to include this in the default setup - I mean not everyone uses routers or self-dialing modems.

---

