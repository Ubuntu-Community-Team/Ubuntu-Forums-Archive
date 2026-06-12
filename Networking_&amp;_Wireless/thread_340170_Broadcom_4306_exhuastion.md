---
title: "Broadcom 4306 exhuastion"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by LavaHot on 2007-01-16
I have a CTO Compaq R4000 laptop whose HD crashed on me, hence why I'm trying Ubuntu, and everything works perfectly except the wireless. I've tried almost everything I could find and it either doesn't work, or I run into unanticipated errors that the Tut doesn't cover. I would greatly appreciate any help in this regard as I am just barely above total n00b status as a linux user.

---

### Post by Metaljaz on 2007-01-17
What version of Ubuntu are you using? What is the name of the wireless card you are using?
Once the name of the card is known and the chipset is determined things can get a little 
easier. Run the following commands from the terminal window and make some notes:

lshw  (command for list hardware)

under network copy and paste the description: product: and vendor

iwconfig 

copy and paste the results

---

