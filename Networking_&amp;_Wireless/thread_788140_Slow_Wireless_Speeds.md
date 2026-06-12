---
title: "Slow Wireless Speeds"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Joe of loath on 2008-05-09
hi;

so i've finally installed hardy on my main pc. i love it! brilliant interface, ALMOST [coming to that in a moment] everything works (hell, thats better than anything micro$hite can muster).

so, after having trouble with my 3com usb wireless dongle, i stuck in the belkin card i know to work perfectly on Dapper (with the exception of having to write a script to get WPA to work, but it works :))

the problem is, i'm only getting download speeds a third of what i should be. i checked the link speed, and i'm getting 1mb/s on a 802.11g network. so 1/54th. it's not the position of the pc, as i'm still dual booting windows for games and such, and i'm getting full speed and a brilliant connection. the card also worked perfectly on dapper on my old P2 box.

so, i'm stumped. what the hell could be the problem? the only thing i can think of, is driver efficiency. an open source driver wouldn't be lab tested and refined perfectly, so i would expect a small decrease in performance, but not this.

so, any ideas anyone? the slow browsing speeds are driving me nuts :mad:

thanks,
Joe

p.s. hard wired network wise i'm getting full speeds too. not a general networking problem...

---

### Post by Joe of loath on 2008-05-09
sorry to do this, but,

TTT

has anyone got any ideas?

---

### Post by Joe of loath on 2008-05-09
erk, it took me 5 mins to load this page... its getting slower :'(

---

### Post by jtrindle on 2008-05-09
It's possible that the card is really running at 1M...

try:

sudo iwconfig wlan0 rate 54M

and see if the speed improves temporarily.

---

### Post by Joe of loath on 2008-05-10
yes it has, actually! not as much as i would expect, but web browsing is faster now. i'll have a fiddle and see what i can come up with...

thanks,
Joe :)

---

