---
title: "Implementing user-based download and/or upload limits"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by gilbertr on 2007-06-06
Does anyone know of a good server app to implement user-based download and/or upload limits ?

I have a Ubuntu server running as a router.
Also have a DSL connection with limited download capacity.
Ubfortunately I also have some people in the house (teenagers) who insist on having to download all sorts of é"é"!§è"é....
As a result I now regularly go down to smallband as my limits are breached.
The sit down and talk with teenagers option hasn't resulted in any improvement, so I would like to extned my DSL provider option of limiting my allowance of download/upload traffic to everyone in the house.

In other words, I would like to set up my server so that no-one can have any type of internet access (no http, ftp, p2p, irc, or anything else) without the following :

- user has to 'log on'
- While logged on, all activity, whatever port or protocol it may, is logged
- Amount of usage,, whatever the port or protocol, is logged
- If the download/upload usage of a user exceeds a preset level, internet access is revoked until the quota is reset or augmented.
- Optionally, I would like not only to limit the amount of traffic but also the amount of time they spend on the internet

Can anyone help me or point me in the right direction ?

Thanks.

---

### Post by fmriguy on 2007-08-01
I wish I had an answer, but I'm hoping to bump this post to see if anyone will respond.  I was hoping to implement a similar system to limit upload bandwidth by user and port.  I found this [howto]("http://www.tldp.org/HOWTO/text/ADSL-Bandwidth-Management-HOWTO") on how to limit upload based on packet, but I'm afraid it is a bit too technical.  I was hoping for a bit more plug and play solution.  Anyone else have any input?

---

