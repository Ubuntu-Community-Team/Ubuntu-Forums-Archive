---
title: "Modem dials, connects, but no internet"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by mortram on 2005-05-03
I've successfully connected to my ISP through both the Gnome Networking Panel and wvdial, but I can't get any applications to recognize the connection.  What do I need to do to get Firefox, Evolution, et al working within Ubuntu?

---

### Post by Slapdash on 2005-05-04
Try this

Open a terminal and do sudo pppconfig. Name the connection "provider". Save before quitting.

In teminal run this command

plog -f

then run 

sudo pon 

in another terminal.

So in other words you gonna have 2 terminals open and you are gonna run two different commands first the one in one terminal window and then the other one in the next terminal window

---

### Post by mortram on 2005-05-07
the strange solution was to name the connection something other than "provider", in this case "nocharge".

pon nocharge connects me and I'm able to access the internet through firefox...

the plog command was helpful, I was unaware of it



Now, how to configure the connection via the Modem Monitor?  No luck with that... does it use the pppconfig files?

---

