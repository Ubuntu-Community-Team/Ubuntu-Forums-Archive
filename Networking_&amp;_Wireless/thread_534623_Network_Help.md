---
title: "Network Help"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by Smith oo4 on 2007-08-25
This is not completely a linux problem but a networking question in general and deals mostly with MS tools* (&#8236;because that is what I already have)&#8236;,  &#8236;if you could give me a hand that would be great or point me to a better place to ask.

I am trying to set up a wireless network at home and this is what I have for equipment:

One Windows XP services pack 2  &#8236;desktop, &#8236;this computer connects to the Internet using a  &#8236;56K internal modem (&#8236;the best Internet connection I can get where I live) &#8236;and also has a Canon PIXMA IP5000 &#8236;printer connected to it.

One  &#8236;desktop &#8236;computer that I am current using to test out linux

Two laptops with WiFi cards  (&#8236;and network cards) &#8236;running Windows XP services pack  &#8236;2

An old D-link switch and a D-link WBR-1310  &#8236;wireless G router

Currently I have a wired network set up using the MS network tools on XP and the old D-link switch, &#8236; I have set up a Internet proxy  (&#8236;I think that is the right term) &#8236;to share the  (&#8236;slow ) &#8236;Internet connection &#8236;on the XP desktop. 

I would like to setup &#8236;a network were the two desktop &#8236;uses a wired connection and the laptops  &#8236;uses a wireless connection and all computers can print and access the Internet  &#8236;through the XP desktop.   &#8236;I have gotten a network setup like this  &#8236;using MS network  &#8236;tools &#8236;with file sharing and printing work fine the only problem is that  &#8236;the only computer that can access the Internet is the XP desktop with the internal modem.  &#8236;If &#8236;someone could &#8236;give me some help getting this working right that would be great.


Also my  &#8236;Linux test &#8236;computer dose have a &#8236;56K internal modem &#8236;in it so it could be use &#8236;with linux as the backbone of my home network and Internet connection but if this is the case,  &#8236;I don't know where to start for I am about &#8236;3 &#8236;months new to linux.  &#8236;Any advice about this option (&#8236;advantages,  &#8236;disadvantages,  &#8236;practicality &#8236;and ease) &#8236;would be appreciated.

I am not the most knowledge about computer and networking but I am trying to learn.

Thank you for any help you can give me.

---

### Post by wirelessmonkey on 2007-08-25
In XP go to network connections.... right click your wireless network and select properties, then bridging (maybe just bridging, I don't have an XP box at the moment) and bridge your wireless adapter and your dialup connection.

---

### Post by trash on 2007-09-22
> **Smith oo4 said:**
> This is not completely a linux problem but a networking question in general and deals mostly with MS tools* (&#8236;because that is what I already have)&#8236;,  &#8236;if you could give me a hand that would be great or point me to a better place to ask.

I am trying to set up a wireless network at home and this is what I have for equipment:

One Windows XP services pack 2  &#8236;desktop, &#8236;this computer connects to the Internet using a  &#8236;56K internal modem (&#8236;the best Internet connection I can get where I live) &#8236;and also has a Canon PIXMA IP5000 &#8236;printer connected to it.

One  &#8236;desktop &#8236;computer that I am current using to test out linux

Two laptops with WiFi cards  (&#8236;and network cards) &#8236;running Windows XP services pack  &#8236;2

An old D-link switch and a D-link WBR-1310  &#8236;wireless G router

Currently I have a wired network set up using the MS network tools on XP and the old D-link switch, &#8236; I have set up a Internet proxy  (&#8236;I think that is the right term) &#8236;to share the  (&#8236;slow ) &#8236;Internet connection &#8236;on the XP desktop. 

I would like to setup &#8236;a network were the two desktop &#8236;uses a wired connection and the laptops  &#8236;uses a wireless connection and all computers can print and access the Internet  &#8236;through the XP desktop.   &#8236;I have gotten a network setup like this  &#8236;using MS network  &#8236;tools &#8236;with file sharing and printing work fine the only problem is that  &#8236;the only computer that can access the Internet is the XP desktop with the internal modem.  &#8236;If &#8236;someone could &#8236;give me some help getting this working right that would be great.


Also my  &#8236;Linux test &#8236;computer dose have a &#8236;56K internal modem &#8236;in it so it could be use &#8236;with linux as the backbone of my home network and Internet connection but if this is the case,  &#8236;I don't know where to start for I am about &#8236;3 &#8236;months new to linux.  &#8236;Any advice about this option (&#8236;advantages,  &#8236;disadvantages,  &#8236;practicality &#8236;and ease) &#8236;would be appreciated.

I am not the most knowledge about computer and networking but I am trying to learn.

Thank you for any help you can give me.

Any luck with that wbr-1310 yet?
I just got one, plugged it into my mac g4 desktop, hit the share connection(in OSX) for ppp0 to eth0, configured the router as best i could understand but no wireless access from my laptop... documentation REALLY sucks and I am gettin really frustrated.

I also tried to set it all up in linux but same outcome.:confused:

---

### Post by trash on 2007-09-22
OH lord... Mark at D-link tech support by phone says it can't be done but then says perhaps send an email to tech support to see if anybody has some advice.

I guess i'll keep playing with it but if anybody has some advice i'd LOVE to hear it!

---

