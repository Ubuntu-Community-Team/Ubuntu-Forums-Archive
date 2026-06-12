---
title: "Switch from &quot;Managed&quot; to &quot;Monitor&quot; and back"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by mrchrisblau on 2007-05-04
I was messing around with airodump-ng and it asked me to put my ath0 into Monitor mode by doing this:

```
 airmon-ng stop ath0
 airmon-ng start wifi0
```

So I did and everything was fine. Now I want to go back to using my wifi card for web surfing (which, i assume, means turning it back to Managed). 

How do I go about setting my wifi card to Managed?

---

### Post by Floppyjoe on 2007-05-04
Have you tried:
```
sudo iwconfig ath0 mode Managed
```

---

### Post by eiapoce on 2007-05-04
> **Floppyjoe said:**
> Have you tried:
```
iwconfig ath0 mode Managed
```

Put the "SUDO" in front of it! 

Enrico

---

### Post by mrchrisblau on 2007-05-05
I feel like I tried that before.

I also feel stupid.

Thanks!

---

### Post by Floppyjoe on 2007-05-05
> **eiapoce said:**
> Put the "SUDO" in front of it! 

Enrico
Done and Done!

---

