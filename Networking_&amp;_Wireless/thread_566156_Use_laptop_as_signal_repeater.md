---
title: "Use laptop as signal repeater"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by dresnu on 2007-10-03
I don't even know if this is possible but anyway.
I have a wireless connection at home, but the signal in my room is very low and I have problems connecting with my mobile to internet (I need it for voip).

Now my laptop, probably because of the bigger antenna gets a better signal.
What I would like to know is if I can use my laptop as a signal repeater for the access point so that I can access the net with my mobile through it (which in my mind will have a more powerful signal) and not directly from the access point.

Is this doable? Could someone point me out what to search for (software?) ? Because I don't even know exactly how to search this piece of information to be honest.

PS: The obvious point of my idea is not to use (buy) extra hardware of course.

---

### Post by kevdog on 2007-10-03
Im sure there is a way to do this, however another method would be to use dd-wrt with another router- which of course would be another piece of hardware -- which you want to avoid.  It might save you some time and headache however.

---

### Post by Lambert on 2007-10-03
> **dresnu said:**
> I don't even know if this is possible but anyway.
I have a wireless connection at home, but the signal in my room is very low and I have problems connecting with my mobile to internet (I need it for voip).

Now my laptop, probably because of the bigger antenna gets a better signal.
What I would like to know is if I can use my laptop as a signal repeater for the access point so that I can access the net with my mobile through it (which in my mind will have a more powerful signal) and not directly from the access point.

Is this doable? Could someone point me out what to search for (software?) ? Because I don't even know exactly how to search this piece of information to be honest.

PS: The obvious point of my idea is not to use (buy) extra hardware of course.

search for "wireless adhoc" but the way you explained I don't believe this is possible. You need one wireless card to connect to the router and another wireless card to run in adhoc mode giving a route for the signal. I don't believe the same card can run in both modes.

Some cards/drivers won't run in adhoc mode so you'll have to find if your card is even capable of it.


Knowing you don't want to buy any hardware, there are some low cost items like this belkin repeater you could pick up.

[http://www.provantage.com/belkin-f5d7132~7BELR018.htm](http://www.provantage.com/belkin-f5d7132~7BELR018.htm)

---

### Post by dresnu on 2007-10-03
Thank you both!
I've searched around too and found no info on the subject. Apparently nobody has ever done this, most probably because it is impossible. The closest solution I found is to plug another wifi adapter, like a pcmcia (which I have but not with me right now), and use the pc as a bridge between the two networks.

But as I said I didn't have a spare card with me now and I was forced to find another solution.

I found it, using good old... aluminum foil! :lolflag:
I made a foil construction around the router's antenna to make it a little bit more directional and surprisingly I get a better signal quality now! :)

Signal power is almost the same as before but noise power has dropped almost 15dbs!

---

