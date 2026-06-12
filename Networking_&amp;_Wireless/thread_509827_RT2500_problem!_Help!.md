---
title: "RT2500 problem! Help!"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by Sparky222B on 2007-07-25
I can see a list of wireless networks in Network Manager, but when I try to connect, nothing happens. Any ideas?

My best guess was this:

I've got an empty pcmia/config.opts file and an rt2500-based (ASUS) wireless card. What should I put in it?

IE, from the docs,

```
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)
  bind "ath_pci"
```

except for my chipset.

What's the right info?

---

