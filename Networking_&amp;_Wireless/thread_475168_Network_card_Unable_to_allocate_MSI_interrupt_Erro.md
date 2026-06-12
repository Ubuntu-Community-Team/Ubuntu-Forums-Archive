---
title: "Network card: Unable to allocate MSI interrupt Error: -22"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by wolfstu on 2007-06-15
So I've got my brand new Kubuntu install on my laptop, and it pauses hangs for nearly a minute in the middle of bootup -- the "Kubuntu" splash screen shows up, and the blue progress bar makes it to about 40%, sits there for a minute or so, and then it goes back to booting and everything's fine.

Wired networking on eth0 works.  Wireless on eth1, I can't test just now without a wireless router.

dmesg includes this line (among a pile of seemingly unrelated stuff) :

```
e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
```

Specs:
Intel Core 2 Duo T5600 1.83GHz
RAM: 1 GB
Ethernet controller (eth0) : Intel 82573L Gigabit Ethernet Controller
Network controller (eth1) : Intel PRO/Wireless 3945ABG Network Connection (rev 02)

Anybody have any idea what's up with this?

---

