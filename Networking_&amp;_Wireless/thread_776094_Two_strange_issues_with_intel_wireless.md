---
title: "Two strange issues with intel wireless"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by bogoliubov on 2008-04-30
Hello. I have a laptop with an intel wireless card. It's working, but I have to really strange issues with it.

1. It's making the router go bananas! When I do software update, the router usually crashes! I have no idea why. But this happened on my iBook as well, but only under Ubuntu, not OS X. So it seems it's a problem with Ubuntu. But mostly when doing software updates. Still, it's extremely annoying!

2. I have to be close to the router to get a connection. 4-5 meters and the router is found and connected without any problems. More than this, and nothing is found, or it can't connect. Now, if I stand close by and let it connect, then move away, it still works! When I get back to where I couldn't get a connection, the link quality is around 60/100.
This is also really annoying, and it's a bit embarassing when showing off Ubuntu to friends and it can't even find a wireless router!


Any ideas/solutions are appreciated!

---

### Post by bogoliubov on 2008-05-03
No one...?

---

### Post by helgman on 2008-05-03
Since no one else wants to look into this you seems to want some kind of an answer I'll give you one, though not a very good one.

> **bogoliubov said:**
> 1. It's making the router go bananas! When I do software update, the router usually crashes! I have no idea why. But this happened on my iBook as well, but only under Ubuntu, not OS X. So it seems it's a problem with Ubuntu. But mostly when doing software updates. Still, it's extremely annoying!

I've heard a lot about trouble with wireless equipment that goes in the "home users" range. Mostly it's caused by bad (cheep) components and not the best engineering (from what I've heard from people in the industry). I agree that it's strange that this only happens when updating Ubuntu. What about big downloads/heavy load in general?

> 2. I have to be close to the router to get a connection. 4-5 meters and the router is found and connected without any problems. More than this, and nothing is found, or it can't connect. Now, if I stand close by and let it connect, then move away, it still works! When I get back to where I couldn't get a connection, the link quality is around 60/100.

I'm no master at the wireless part of Ubuntu (or Linux) but have you played around with iwlist and tools like that. Are there a lot of wifi-networks in your area (there could be other networks on the same channel)? What kind of wifi-card are you using (on-board, PC card, USB etc)?

I've had terrible problems with a few PC Cards that just won't pick up a signal if I'm more than a few pases away from the AP (and sometimes line-of-sight and tre meters are more than it can take). But that's never been specific to Ubuntu ...

I know this is not much help but it might be a start ...

Regards,
Helgman

---

### Post by bogoliubov on 2008-05-03
Well, the wireless "card" is somewhere in my laptop, so not an USB thingy. I can copy files within my LAN without any problems. I can also download stuff with Firefox or with Bittorrent and the router is OK. But software update = problems!

There is only one more wireless network around my home, but I'll have a look at iwlist. I'm not sure how to check the channel of the other wireless network though...

Thanks

---

