---
title: "ndiswrapper not detecting my dwl-g630"
date: 2005-05-29
forum: Networking &amp; Wireless
---

### Post by spicychicken on 2005-05-29
Thanks for the help,

Just installed 5.04 on my laptop.

now I'm trying to set up my pcmcia wireless card

D-Link DWL-G630 with ndiswrapper

ndiswrapper -l shows

Installed ndis drivers:
net5211 driver present

but does not find the hardware - if I got into device manager i can see my wireless card.

i have the latest xp drivers for the card and wireless-tools and pcmcia-cs is installed and both are the latest versions.

I investigated the following bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

but I could not get the warty version of pcmcia-cs to work either.

any and all help would be very much appreciated....

Thanks!

---

### Post by spicychicken on 2005-05-29
so it ends up I did not have hte latest driver .... if you have this problem makes sure you go to dlink and get the latest and greatest.

---

