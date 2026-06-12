---
title: "[SOLVED] Azureus strange connectivity issues.."
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by loverman210 on 2007-12-04
Hello everyone...

I am a newbieand here is  my new problem... (I have already posted this in the "absolute begginers" but still not a descent answer so I thought it would be more appropriate here..-sorry for doubleposting)

I installed azureus 2.5.0.4 and have set a static internal ip 192.168.1.45 and opened a port 53565..

The Problem is that while azureus doesn't have any NAT or reachability problems, it takes extremely long to load and when it's done everytime it loads keeps poping up a message:

<<There appears to be another program process already listening on socket [127.0.0.1: 6880]. Loading of torrents via command line parameter will fail until this is fixed.>>

But the thing is I don't run any other programs!! Only one at a time and right now it's azureus...

--When I had **the router** choose my internal IP,  I was using ```
ifconfig
``` to see which one was, and then I forwarded the port in the corresponding one...--

*Note that this problem started from the time I set s static internal ip so that I could properly forward my port...and not change the settings all the time...

any help would be really appreciated...--in very simply english words please! :lolflag:

thnx in advance..

---

### Post by loverman210 on 2007-12-05
never mind...

used deluge instead...worked like a charm..!!

---

