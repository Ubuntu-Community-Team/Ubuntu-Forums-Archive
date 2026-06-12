---
title: "Problem with aDSL connection in 7.04"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by bulletshot60 on 2007-10-23
Ok I have Feisty Fawn.  I used to have a dial-up connection that worked excellent.  Then, I upgraded to bellsouth DSL (PPPoE).  I was sent a Westell 6100 modem that I set up.  Then I proceeded to install the programs required on my XP (I have a dual-boot.)  The connection works great on my XP (I am using it to post this) but Linux detects the new connection but fails to set it up.  Using pppoeconf under root returns no found eth0 interfaces access contributers, but the interface does exist.  However, I have tried inserting my IP into networking, but that failed as well.  The connection is there, I just can't use it.  Also, for some reason the ethernet light on the back of the computer does not light up when using linux and the modem lights up only power and DSL meaning nothing is being found or going through.  I know I just rambled quite a bit, but please help.  If you need more details, just post what you need and I'll try my best to get it to you.  Oh, and the connection fails when using the live CD as well.  And it doesn't matter whether I am using USB or Ethernet still no connection. :confused:  Please help. :confused:

---

### Post by bulletshot60 on 2007-10-24
Okay, I solved my problem but I still do not understand it.  My ethernet still does not work. However, my USB works but not with Fiesty.  I found an old copy of Dapper Drake and found it worked using eth1 interface.  Could someone please help set this up in Feisty so that I can use Feisty until the next LTS release in 2008.  Thanks in advance.

---

