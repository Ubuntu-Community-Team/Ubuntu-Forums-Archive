---
title: "Internet fail after 6000 mile move"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by JiuJitsu500 on 2010-03-24
Hey all, haven't been on in a while, busy taking vacations and schools and what not... so to not bore you, I ran into an interesting problem.

I'm just looking for suggestions too, I haven't actually been on these computers yet, work says I go back on the 6th of April so I have time to look into it first... They didn't tell me about it either till about three days ago... so it's their problem for sure until I get to it.

About 4 months ago or so, I installed 9.10 with huge success on somthing like 20 laptops in Iraq with my unit (Army guy...) and loved figuring their problems out as much as mine. Love Linux, Love Ubuntu, love the whole thing and almost every one of them have kept it (one Mac guy couldn't deal with it, too used to their great system, and a couple guys I gave Windows 7 to in order to keep them happy and away from Vista).... and only two of them remain a problem now, but they refuse to step away from this OS as they find it... simply... better... :)

Anywho, the LAN line internet worked fine in Iraq, even our Ad-Hoc networks we'd set up all the time to cure the boredom bug. But, after our return to the US in January, two laptops, both different brands (maybe with the same card though?) cannot seem to connect to the internet at all, wireless, ADHOC, LAN, nothing.

It's odd, and I think they want to wait for Lucid anyway for a fresh install, but they would like their internet.... I was going to remove the original internet manager and install WICD for it, but just in case that fails... anyone have any other ideas?

---

### Post by jimv on 2010-03-25
The first thing to check is make sure that they're getting IP addresses from whatever router that they are hooked up to.  If they are, then see if they can ping anything via IP address.  If not, they might have static IP addresses set.  If they can, then check if you can ping anything via DNS name.  If not, it's a DNS issue and could be an issue with having DNS configured manually instead of automatically.

---

