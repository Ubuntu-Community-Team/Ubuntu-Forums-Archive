---
title: "Recommended wifi dongles for Feisty 7.04, anyone? I'm buying..."
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by br3nd6n on 2007-06-20
I've installed Feisty but I gather from the very telling poll (at [http://ubuntuforums.org/poll.php?do=showresults&pollid=1806](http://ubuntuforums.org/poll.php?do=showresults&pollid=1806)) that *most* people are having trouble with wireless networking on it.

I'm looking to buy a new USB wifi dongle (unless you'd advise otherwise) but I'd rather not have to faff about getting it to work. 

Any suggestions?

I'd pay extra for one that will install first time around. I'm new to linux and don't really have a great deal of time on my hands.

Thanks!!!
Br3nd6n

---

### Post by scrooge_74 on 2007-06-21
Check this [list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") before giving your money away.

Better not buy USB wireless, PCMCIA works best

---

### Post by br3nd6n on 2007-06-25
Thanks very much - but that doesn't answer my question unfortunately. :(

Firstly, that list includes loads of irrelevant and out of date info on previous versions of linux - but my problem is Feisty, which is, it seems, quickly becoming renowned for its poor adaptability to various wifi adapters that worked on previous versions.

And secondly, I'm using a desktop, not a laptop - so unless I'm mistaken I couldn't use a PCMCIA card (it'd have to be a PCI card)...

Any other suggestions, anyone?
B

---

### Post by smoocat on 2007-07-16
I'm in the same boat as you, after having trouble with my Netgear WG111v2 USB dongle..  Though I did have to go through some loops making it work well on Feisty, it's now having issues with my other OSes (XP, Vista) as well.  The dongle is apparently notorious for overheating, which I suspect has something to do with its dropping connections all over the place.

Anyway, to cut that long story short, I'm now shopping for a PCI adapter (I've got a desktop, too).

This [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion") seems to have a pleasantly small and updated list of adapters, and even has a column for future Gutsy Gibbon compatibility.

If you're looking for good value, check out the Trendnet TEW423PI PCI adapter (do a quick Amazon search..).  It doesn't work out of the box on Feisty, but with a bit of configuration on ndiswrapper you've got yourself drop-free wi-fi for $20.

Best of luck on the search.

---

### Post by scrooge_74 on 2007-07-16
Sorry I could not help much, and you are right about Feisty and it management of wireless adapter, I had to do a lot of tweaking to get mine working and a couple other laptops I have I have kept them from using Feisty to avoid the extra work. (One is still using Dapper and the other is on edgy)

---

### Post by Leftblank on 2007-07-17
I won't name this post a bump, but I would like to state I'm highly interested in this as well, I'd like to equip my laptop with an USB wifi dongle, though it's hard to find resources on what ones are recommended, especially considering the ones on the Wiki are rather hard to get here in the Netherlands or very expensive - which is of course also a drawback.

---

### Post by br3nd6n on 2007-07-23
> **smoocat said:**
> ...having trouble with my Netgear WG111v2 USB dongle...apparently notorious for overheating, which I suspect has something to do with its **dropping connections all over the place**.


Interesting what you say about dropping connections. I've ended up being given a BELKIN USB F5D7050 which has, to my great surprise, 'worked' out of the box. Sadly, it drops the connection left, right and centre. And the bizarre thing is that when it's not dropping the connection, it's saying that the reception is between 95% and 100%. Then it'll suddenly drop to 0%, disconnect, and reconnect again in the next couple of seconds - not a great deal of use!!!

So my thinking is this: is it a bug in the drivers, or is it Fiesty, or do the two of us 'just happen' to have faulty/weak/pathetic dongles?

Anyways, I suppose I should probably be looking in other threads now that I've actually got a driver.

Thanks to all for your suggestions!!!

B

---

