---
title: "Problems with DLink DWL G122 r3"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Kceltyr on 2008-07-24
Okay, this is the last resort, I've up to now been proud of the fact I've been able to research most of my problems and fix them myself, but this one has me stumped. I've spent the last 5 and a half hours trying to get this one nutted out...

So, I had this other card, it worked with NDISwrapper fine, but the card itself had really bad reception. A mate let me borrow his G122 r3 while I got my own. That one plugged straight in and worked fine. Happy days.

Today my G122 rocked up and I stuck it in, pulled out my ethernet cable, just like I did last time. I click a link, it load, albeit extremely slowly. I go to google to work out why it's so slow. Timeout. Check signal strength in NM, over 80%. emesene dies on me, then GMail. So I go check on another computer that the net is fine; it is. So I reconnect to the wireless network, same thing. 30 seconds of connectivity, then it dies.

After a lot of searching the main points are:
I got rid of the old NDISwrapper drivers from my old card, and physically removed my old card.
I tried downloading the drivers from serialmonkey for Ralink chipsets. When I iwlist I get wlan3, not ra*** like all the walkthroughs suggest I should have. When I scan with iwlist it gets no results, but nm-applet gives me 80+% strength.

What makes things hard is that all the walkthroughs are for people who's card has not been detected, whereas I've actually achieved brief connectivity, albeit at a slow speed.

Anyone got any tips at all? Links I may not have come across yet? this is frustrating the hell out of me. It worked before and nothing has changed except the Ubuntu updates which, come to think of it, actually updated the kernel.

Now off to try install artwiz fonts... not ready to concede defeat on that one yet...

~James

---

