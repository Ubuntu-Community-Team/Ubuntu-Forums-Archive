---
title: "3Com EtherLink III PCMCIA 3C562D/3C563D showing up on eth0 but not working.."
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by glósóli on 2008-06-27
Hi all!!

I've got an old, old laptop that I wanted to bring to new life, since its low power consumption. Its destination would be a 24h/24 server..

the ethernet is an old PCMCIA card by 3Com EtherLink III, and it's 100% working!

i installed alternate xubuntu, and everything went fine...
just a bit too slow, but my projects are to let it run just in text mode, as it will be screenless.

but, the primary thing for a serve is network, and so far I wasn't albe to bring it to work!

In fact, if I make ifconfg eth0, it does show all the infos, the IP I gave and so on...but I wasn't able to ping my router, both in static and dhcp mode.

tried to restart eth0, removing and reinserting the pcmcia card, but nothing.

so, what could it be the cause?
3 days before I also tried DSL, and networking was ok; so the hardware is good.
although DSL is lighter, I'd prefer xubuntu for its wider support and user-friendly: really didn't know to start out to set up the amule daemon with DSL...

thank you guys!

---

### Post by glósóli on 2008-06-29
nobody has got any hint? :(

---

### Post by Iowan on 2008-06-29
Haven't tried it with post-Breezy versions, but I was unable to get one of my machines to recognize an ISA 3C509B card with out-of-the-box install.  I didn't research additional drivers - perhaps your PCMCIA card is in the same boat (needs additional/different drivers).

---

### Post by glósóli on 2008-06-30
mmhh, it would be quite painful to me searching new driver...
they're hard to find also on xp...

when I first tried DSL, I was really impressed that it recognized it with no problems..

I hoped Ubuntu and his little brothers would have been straightforward too!

---

