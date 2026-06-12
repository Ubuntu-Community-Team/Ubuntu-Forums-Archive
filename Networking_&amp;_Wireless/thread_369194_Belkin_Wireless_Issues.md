---
title: "Belkin Wireless Issues"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by leetcharmer on 2007-02-24
I was using my computer once a couple months back, and the internet worked fine then (the desktop computer has a PCMCIA slot built in it, and a wireless card sticking in).  I booted up last night, and Ubuntu no longer recognizes the wireless card.  I can't edit or do anything with the Networking tools.  How can I add my wireless card again?  I popped in an Edgy Live CD and it doesn't detect my wireless card there either.  I checked the back of the PC and the wireless card's light is on, so I thought it must be working, just like it was back then.  Sometimes when I pop in the LiveCD, it shows 2 WIRED connections, which is REALLY weird.  Mostly though, just 1 Wired Connection and no more wireless shows up.  Any idea why?

---

### Post by spd106 on 2007-02-24
Could you post the output of entering **sudo lshw -class network** at a terminal.

If you sometimes see an interface called wifi0, then it's safe to ignore it as it's a virtual interface that shouldn't really be visible, depending on which tool you use.

---

