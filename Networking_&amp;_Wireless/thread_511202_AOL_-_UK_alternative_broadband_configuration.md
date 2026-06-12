---
title: "AOL - UK alternative broadband configuration?"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by sleepingdragon on 2007-07-27
Is it possible to provide your own broadband modem and supply it with the right details to access AOL in the UK rather than rely on the modem provided by AOL? I'm *guessing* that the BT Voyager 105 is a 'soft' modem, very much like the old-fashoined internal 536/537 56k modems that required software to do the rest of the work. 

If anyone has any ideas on this I would greatly appreciate it. It's not for me (I'm here and online), but I'm trying to help someone who's sick to death of the 'other' OS and would like to avoid endless AV/spyware scanning and bloated firewall software, they would love to convert to Ubuntu (I've been beating them with a stick to get them off my Ubuntu box!), but the AOL connection problem is a bit of a nightmare.

---

### Post by coffeecat on 2007-07-27
I can't answer your question as I have no experience of AOL, but if AOL supplies a straightforward ADSL service I would hope that any standard modem-router would work fine. But you'd need to check this as AOL have a reputation - or so I believe - for doing non-standard things.

Can you borrow a modem-router and try it out on your friend's connection? All you need is the AOL login name and password and you can configure it through a web-browser. If it works with Windows it should work with Ubuntu. And there's an important security advantage to using a modem-router - a decent firewall and NAT.

How much of the AOL contract has your friend left? If s/he wants to convert to Ubuntu and there's a problem with AOL then it seems an ideal time to change ISP. My advice would be to avoid the big boys (Tiscali, Orange, anything with a too-good to be true price) and go for one of the smaller players. [This page]("http://www.thinkbroadband.com/isps.html") from Thinkbroadband makes interesting reading. Have you searched around the Thinkbroadband website? It might have something to say about AOL. There are forums there but I find them disappointing - full of whingeing bit-torrent downloaders who are annoyed at being rate- and speed-capped. :twisted:

---

### Post by ugm6hr on 2007-07-28
This suggests some ADSL settings - can't guarantee they'll work though:
[http://help.aol.co.uk/configure-your-modem-router-thomson-speedtouch/article/20070405105409990007](http://help.aol.co.uk/configure-your-modem-router-thomson-speedtouch/article/20070405105409990007)
VPI: 0
VCI: 38
Connection: PPPoE
User: [email]screenname@aol.com[/email]
Password: AOL password

---

### Post by MrHippocampus on 2007-07-28
Any normal ADSL router should work fine with AOL, they pretty much use the same system as everybody else now, all you need is the configuration options posted by ugm6hr :)

---

### Post by sleepingdragon on 2007-07-29
Thanks for the link! I'll give it a go and keep you posted.

---

### Post by ugm6hr on 2007-07-29
> **sleepingdragon said:**
> Thanks for the link! I'll give it a go and keep you posted.

If it doesn't - try calling AOL customer support and asking them for the ADSL settings.  It is poor that they don't make the settings clearly available from their website.  Threaten to disconnect if they won't oblige - that usually works with them (and often gets you an extra month free!)

---

### Post by sleepingdragon on 2007-10-21
OK, it's been a while since I replied to this thread, but I've got it working!

I've gone with an alternative wired modem  - Linksys AM200. This doesn't contain a router but does have all the good configuration settings. Simply connect and follow the nice 'n' clear user guide to point your web browser to the modem settings page.

Now for AOL. Go to this [[COLOR="Red"]page[/COLOR]]("http://help.aol.co.uk/what-are-the-essential-settings-for/article/20060802092709990038") and follow their instructions - yep, you read it right, AOL are providing settings for modems other than their own.

Works a charm, and in case you're wondering, the AM200 modem is about £20-£25 in the UK and works very well.

---

