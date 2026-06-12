---
title: "cant get wired connection"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by skeeredandconfuzed on 2007-10-18
just installed gutsy, got to desktop... no network connection.

i reset the router (d-link di 624), and notice... my port lights not on. power, wan, wlan are on but #1 isnt, i try port #2.. no go. lather rinse repeat. 

dual booting with vista, switch over and im online.. my port light #1 is on now.. means router and cord are fine.

seems like gutsy does not recognize my nic? sumthin like that? feisty and edgy worked just fine with the exact same rig/router/modem/etc...

advice? instructions? reassurance?

im techie, but not too techie... so plz try to talk to me like im a kid.
thnx

---

### Post by amcp21 on 2007-10-19
the same happens to me

I have NB Acer Aspire 5100 with a Realtek RTL8139 lan card totally disabled

The weird is my wireless is all functional

what happens?

---

### Post by skeeredandconfuzed on 2007-10-19
figured it out.. 

apparently vista, in its infinite wisdom, shuts down the actual nic when it shuts down the pc..

they say its power saving, i say it monopolism

i found a thread that said to go to network connections in windows -> properties -> and find the settings that allow it to do that, and turn them off... i tried, didnt solve the problem.

i ended up simply booting vista, then unpluggin the whole pc, so it would shut off without goin through all of m$'s shutdown procedures...

sure enough, i plug it back in, go to ubuntu, and im online :)

so bottom line, this prob is caused by windows doin a power-savin nic turn-off magilla, and that would be the tree to bark up...

happy huntin:)

---

