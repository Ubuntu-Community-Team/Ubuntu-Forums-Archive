---
title: "Unsecured Network Shows as Secured... Sometimes."
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by coldstatue on 2008-08-21
I am running Hardy with an Atheros AR5000EG Wireless card, but have similar issues when I boot into windows. 

I am currently using Mad Wi-Fi, though I have the same problem with NDISWrapper. Wi-Fi Radar doesn't help - can't get IP address.

My job has open wireless. It works for my wife, it works for my coworkers. Everything is fine on their end. My computer connects... sometimes. In Ubuntu, if I am lucky enough to see it as an unsecured network, I can connect. If it shows as secured, I cannot. It's a 50/50 shot. 

I thought I might be seeing another, secured, network with he very generic default name of linksys, and not seeing our unsecured one, but I never see 2 networks named linksys. 

When in windows (very rare) I will see one secured and one unsecured. I would assume there are two networks, but my wife and coworkers have no such problem.

I have an Acer 5520 5290, which (I found out after ordering the mini-pci IBM 2200) uses mini-pci express. I am unfamiliar with this standard. Is there a card in this format that works out of the box like the 2200?

Any other suggestions?

Not sure what output I should post here but restarting the networking doesn't even disconnect me:

```
$ sudo invoke-rc.d networking restart
[sudo] password for coldstatue: 
 * Reconfiguring network interfaces...                                          eth273: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth273.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth273: ERROR while getting interface flags: No such device
eth273: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device

```

my wireless card is wlan0.

I usually just have to wait, and it will come up... sometimes minutes, sometimes hours. 

Any thoughts/suggestions are greatly appreciated. 

Thanks.

---

### Post by changintimes on 2008-09-03
i have the same problem with a linksys signal......or 2 ? 

same thing, unsecured sometimes (and i can connect), or secured sometimes (and i can not connect), 

did a google search to find your thread, i registered here just minutes ago, 

all i can say is, i move the antenna around a bit, and refresh my network signal list, and sometimes i get the unsecured linksys signal, then i connect, 

i thought maybe it's 2 signals too, but are they in the same room ??? my antenna seems to be in almost the same place when the 2 linksys signals alternate from secured to unsecured, 

does anybody know what else can be happening here ?

---

### Post by coldstatue on 2008-09-03
change the L in linksys to a capital on one network.. the two will no longer be confused

---

### Post by changintimes on 2008-09-07
yes but i'm just tapping into the unsecured network, i don't think changing anything will make a difference,

---

### Post by coldstatue on 2008-09-07
The problem is, assuming yours is the same as mine, that there are 2 networks named linksys - 1 secured, 1 unsecured. For some reason, NM only sees one of those at a time. I just waited until I could connect, logged in via firefox at 192.168.1.1, using the default blank user ID and pass of admin and changed my network name to Linksys so I wouldn't have to bother with anything else. Works for me.

---

### Post by changintimes on 2008-09-08
well i don't think i'm as comp savvy as you, but i will try your directions, 

i don't know where the linksys routers are, i don't know where the signals are coming from, but there are 2 signals, seemingly, 

linksys unsecured, 

and

linksys secured, 

pretty cool though that we seem to have the same situation,

---

### Post by coldstatue on 2008-09-08
Well, I'm not *that* savvy. My solution might not work for you. i just figured out what worked for me, and that network manager can get two networks confused if they share a name.

---

### Post by changintimes on 2008-09-09
i understand the 2 names being thought as the same signal part, 

i just don't know how, or if i should, change the name of the signal from linksys to anything else, 

i could use the linksys default access key for other signals, and netgear as well,

---

### Post by coldstatue on 2008-09-09
I'll assume you have a crazy setup with tons of routers in your place, because I would never encourage illegal activities.

Changing the name won't screw anyone else up, because there are basically no settings needed to connect to an unsecured network. Instead of being automatically connected next time they boot, they'll just have to select Linksys, without ever noticing the change from lower-case l to capital L. 

Connect to the unsecured linksys network. 

open your browser and go to 192.168.1.1 like you would any website.

You will be prompted for a user ID and pass. Leave user ID blank and type admin for the pass. 

In the top row of options, click "wireless"

change 	 Wireless Network Name(SSID) from linksys to Linksys.

Click "save settings" at the bottom.

check what wireless networks are available now.

You still may only see 1, but if it has a capital L, I think it will be unsecured. 

It might fix your problem... might not. You can always change it back.

As far as the default access key, I really only know linksys - which is no key at all. maybe you meant the pass to access router settings. If you see an unsecured network named linksys, I'd bet a dollar any day that the pass has not been changed. Of course, I would only check that on my own router. 

see this: [http://answers.yahoo.com/question/index?qid=20071127120832AAzjHme](http://answers.yahoo.com/question/index?qid=20071127120832AAzjHme)

then see this: [http://www.wired.com/politics/security/commentary/securitymatters/2008/01/securitymatters_0110](http://www.wired.com/politics/security/commentary/securitymatters/2008/01/securitymatters_0110) I don't remember the name, and it could well be listed in this article I didn't just re-read, but there is a website where people willing to share their wi-fi post a rough address to a searchable database. 

In the end, unless you're in some temporary emergency situation, comcast is pretty cheap and easy... it's also legal.

---

### Post by coldstatue on 2008-09-09
check this, apparently legal project

[http://www.fon.com/en/info/whatsFon](http://www.fon.com/en/info/whatsFon)

---

### Post by changintimes on 2008-09-15
crazy stuff, there must be a catch, 

went to Linksys from linksys as you said, got scared that they locked it up, could not get the unsecured signal for about a day, i sure don't know what happened, i did only leave it as Linksys for about 15 minutes, then went back,

---

