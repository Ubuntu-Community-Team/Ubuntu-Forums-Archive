---
title: "Wireless works, ethernet doesn't..."
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Starks on 2008-02-18
How do I solve this?

Ubuntu 8.04 Hardy Heron
Linux kingfisher 2.6.24-8-generic #1 SMP Thu Feb 14 20:40:45 UTC 2008 i686 GNU/Linux

---

### Post by nixscripter on 2008-02-21
I would start with some diagnostics to try and isolate the problem. If you have more specific symptoms, please describe them, and some of this can be skipped.

1. If there is a light on your ethernet card visible, see if it turns on when you connect it to something. If not, it's probably the card's fault.

2. Open hardware information (I think it's under Ubuntu  Menu -> System -> Administration -> Hardware Information) and see if the ethernet card is in the list. If not, it's probably a driver problem.

3. Otherwise, it's probably a configuration problem. Open up a terminal, and post the output of the command:

```
ifconfig -a
```

---

