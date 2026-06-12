---
title: "Software to tell me whos on the network, how much bandwith theyre using etc"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by jgrabham on 2007-08-03
I want to see who's using my network, and if they're slowing it down, what they're using, how much theyre downloading from the internet etc.  Are there any apps which can monitor this.  (Im not on a server or anything, just a desktop PC connected with a cat5 cable to my adsl modem router, which has windows PCs accessing it via wifi)

---

### Post by jgrabham on 2007-08-03
Guessing I cant get anything then

---

### Post by HermanAB on 2007-08-03
Well, first of all, you need a hub, not a switch, so that all network traffic actually gets to your Linux machine.  Then simply use tcpdump.

Cheers,

Herman

---

### Post by splintercellguy on 2007-08-03
A router should be able to report what clients are connected.

---

### Post by callan79 on 2007-08-04
> **jgrabham said:**
> I want to see who's using my network, and if they're slowing it down, what they're using, how much theyre downloading from the internet etc.  Are there any apps which can monitor this.  (Im not on a server or anything, just a desktop PC connected with a cat5 cable to my adsl modem router, which has windows PCs accessing it via wifi)

Well, I guess the solution depends on exactly what you need...

CACTI - [www.cacti.net](http://www.cacti.net) - will be able to tell you the bandwidth being used by each device on the network. The devices you want to monitor must support SNMP as this is how Cacti gets its data. Windows XP does support SNMP, so do most other operating systems, but you have to enable it.

A PROXY SERVER - if you set up an Ubuntu box as a network server, then instead of everyone getting Internet straight from your router/modem, they go via your Ubuntu server, then you can log everything on there. I'm not sure how, but it can be done. Back in the dialup days I did this with IPCOP - [www.ipcop.org](http://www.ipcop.org) and this told me exactly which websites everyone was looking at.

Hope this helps

Callan

---

