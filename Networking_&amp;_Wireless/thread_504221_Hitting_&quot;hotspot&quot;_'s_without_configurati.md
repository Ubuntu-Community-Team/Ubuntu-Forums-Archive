---
title: "Hitting &quot;hotspot&quot; 's without configuration"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by KamakazieX on 2007-07-18
I am in the process of building an embedded system with Intels MiniATX celeron system (89 bucks on newegg).

I am trying to design an embedded linux setup based off of either the new Debian 40r0 (which I praise) or Ubuntu 7.04 (which I have been using since 5.04 and praise the community support and repo's). ..Here is the scenario:

You have an embedded system and in dash LCD monitor in your car; no time however, to play with the keyboard or click here and there. You add "x" wireless pci card (which I still dont know what to get).

I need a solution where a script with administrative rights would sort of be used as a wireless heartbeat, and once it found an OPEN (not cracked) network it would attempt to connect and stay connected until the signal threshold was below x% or just lost in general. Here is an example.

Your a consultant, always on the road, you have your embedded system set so you can stay in close contact with buisness or whoever. Your on your way home from work. (Events happen while your driving -- your embedded sys in your car detects that an open wireless network is available, automatically connects, syncs your emails, grabs offline messages, and some rss feeds.) So your in dash console alerts you new events have happened - 3 new emails - bush learned to spell - bob is hammered in vegas. With me here?

I guess the whole thing is intention, this would be more along the lines of wardriving, but only connecting to those networks that allow you the basic "plug 'n pray". If it were any more complex than that it would ignore it and go on to heartbeat for the next open network. Eg, that coffee shop at the center of town, the dealerships on the way home. Or, that random place in NY where you got stuck in a traffic jam.

Anyone like my idea?

Maybe even extend it, where you have an exception list, eg, your at home and you HAVE a secured wireless network, so you have something like wexempt.conf somewhere in \etc. Where you put the mac addr of the AP in your garage,, so everythings good when your car's warming up in the morning or right as you drive off.

---

### Post by t4thfavor on 2007-07-18
There was something like this developed for the wrt54g. It as marketed on Ebay as bluebox, or bluefox. I believe you could adapt the scripts to your likeing. 

It is open source, they just want you to pay for the advanced version.

---

