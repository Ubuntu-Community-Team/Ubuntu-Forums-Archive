---
title: "Ubuntu now won't connect to my BT Home Hub"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by Digital Spaghetti on 2007-08-29
Hey folks,

I've been using Ubuntu fine now since January, but in the last few days my laptop has been refusing to connect to my BT Wireless Home Hub.

I've actually just freshly re-installed Ubuntu on here, but just before I did I took my laptop into work and it connected fine there, I've then brought it home with the fresh install and it refuses to connect.  My XP Machine is also connecting to the wireless point fine.

The BT Home Hub uses 64b HEX WEP, and it finds the point but refuses to connect.  I've reset the box to factory settings to, and sat and watched on my XP PC my laptop connecting, and then disconnecting again.  I also tried a second box I have that's not usually plugged in, and the same thing happened.

DHCP is on on the box, and I've added the IP to the DNS.

Anyone else had similar problems?

---

### Post by ddrichardson on 2007-08-30
I've a home hub that sometimes does the same thing, reseting it didn't work at first so I cut its power and left it half an hour then turned it back on and it worked fine.

I've been keeping an eye on it and I'm not sure whether its a heat related problem or a problem with how BT sends the firmware upgrades.

Software Release:6.2.2.6
Software Variant:AN [IMG]http://bthomehub.home/images/spacer.gif[/IMG] 
Boot Loader Version:2.0.3 [IMG]http://bthomehub.home/images/spacer.gif[/IMG] 
Product Code:3610739C     [IMG]http://bthomehub.home/images/spacer.gif[/IMG] 
Board Name:BANT-Z

I must say I have found this to be the most tempremental router I've ever used and it seems to be all of them (every year or every billing mistake BT makes results in another complementary Hub and Phone!).

BTW - How's the festival going - one thing I don't miss about my home town is the tourists, especially those who ask what time the one o'clock gun goes off.

---

### Post by Digital Spaghetti on 2007-08-30
Yea, I have the latest firmware.  I've just hooked up my PC to the ethernet just now, so I can get access.  I'll try the turn it off for 30 mins and see how that works.  Your correct though, I've had two now - and I find lots of issues like it cutting service, major slowdowns and other major problems.

---

### Post by menotknow on 2007-09-03
Is there an idiot guide to set up with a wireless conection to a  BT hub?

I really do mean idiot guide I am new to Linux and this is all new to me, so as step by step a guide as possible.

I have Unbuntu 7.04 on the machine I am trying to conect.

Thanks in advance for any help

---

### Post by ddrichardson on 2007-09-04
Well you don't need a specific guide because the Home Hub is simply a 64 bit WEP enabled router that uses DHCP.

If you are having difficulties then its most likely in the configuration or detection of your wireless card.

There's a wealth of information on this here and in the wiki. Can you start by posting the output of```
lspci
```

---

