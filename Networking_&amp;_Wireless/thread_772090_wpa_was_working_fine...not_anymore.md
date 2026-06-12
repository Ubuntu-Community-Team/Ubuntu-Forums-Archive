---
title: "wpa was working fine...not anymore"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by jaikat on 2008-04-28
hello

i have an acer laptop with an atheros wifi card.
i managed to get it working perfectly with wpa security using WICD manager and wpasupplicant.

everything was going well until the last time i turned off the computer.

yesterday i turned it on and it wouldn't connect. it can see the network, and everything else is in place (configs), but it simply won't authenticate.

i don't know what could've changed, because i'm sure i didn't change anything, and as i said, it was working perfectly..

any advice appreciated..

running ubuntu gutsy
atheros wifi card

---

### Post by jaikat on 2008-04-30
well i just wanted to say that i managed to work things out, although i couldn't find a reasonable explanation to my problem except that either WICD or wpasupplicant were in a "hanging" state.

what happened was i checked the static ip box in the preferences tab in WICD, and tried to connect and walla, it did. i then removed the static ip check and went back to roaming, and.. walla, as if nothing happened..

all i can say is .. walla again..and here's to "trial and error"

---

