---
title: "buy a linux-friendly 54m pcmcia card"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by zjcim on 2006-08-06
i really got frustrated about my damned dwl-650 revP(revP means there is no firmwarn on card ,u shoud initlize the firmware in the driver),
so ,i have to buy a 54m pcmcia card 
Whick brand whic modle would be linux-compatible?

---

### Post by UnixAnt on 2006-08-06
Well, as I am from an techie background I always tried to avoid buying hardware specifically for my OS - preferring to MAKE the card work with my OS instead (and hopefully learn something in the process too).  However, sometimes you simply want/need a quick fix...

I believe anything with the Ralink chipset will work out of the box, although I have only tried this with a desktop card and not a PCMCIA version.  Should be exactly the same principle I would have thought...

I have also had success with Belkin and Netgear 54g cards.  I currently have a USR5410 card which worked fantastically well under 5.10, but required a lot more head-scratching to get working under Dapper.

---

### Post by stormblue on 2006-08-06
The netgear WR511T works right out of the box.

---

### Post by weekend warrior on 2006-08-06
Any of the ones from this [list from the Free Software Foundation]("https://www.fsf.org/resources/hw/net/wireless/cards.html").

Personally, I have a [Belkin F5D7010]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136500") which worked straight out of the box, no setup needed and I'm very happy with its performance.

---

### Post by encephalon on 2006-08-12
> **UnixAnt said:**
> I currently have a USR5410 card which worked fantastically well under 5.10, but required a lot more head-scratching to get working under Dapper.
Did you manage to connect to a WPA encrypted router with this card? I've tried that for at least a week following a dozen of guidelines with no luck, would be very happy to hear the answer...

---

### Post by kphyfe on 2007-01-11
> **UnixAnt said:**
> Well, as I am from an techie background I always tried to avoid buying hardware specifically for my OS - preferring to MAKE the card work with my OS instead (and hopefully learn something in the process too).  However, sometimes you simply want/need a quick fix...

I believe anything with the Ralink chipset will work out of the box, although I have only tried this with a desktop card and not a PCMCIA version.  Should be exactly the same principle I would have thought...

I have also had success with Belkin and Netgear 54g cards.  I currently have a USR5410 card which worked fantastically well under 5.10, but required a lot more head-scratching to get working under Dapper.

I have the head scatching happening at the moment and could use some advice.  What did you end up doing.  I have detected and even have a signal to the 5410 I used the linuxant driver install suggested through the USR support site.  

Any help in this matter would be very much appriciated.  Thank you in advance.

Kent

---

### Post by tturrisi on 2007-01-11
How To Install dwl650 revP:
[http://www.oakcourt.dyndns.org/~andrew/dwl520e1.html](http://www.oakcourt.dyndns.org/~andrew/dwl520e1.html)
"[i]A Note About the DWL-650 rev. P
The DWL-650 rev. P is the PCMCIA cousin of the DWL-520 rev. E. It is a 16-bit PCMCIA 802.11b wireless LAN card. It sports an Intersil Prism chipset and a SSF design. Setup is remarkably similar.[/i]"

---

