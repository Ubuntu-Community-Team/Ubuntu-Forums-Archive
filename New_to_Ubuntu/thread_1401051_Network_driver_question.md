---
title: "Network driver question"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by angeli106 on 2010-02-07
Hi, so i've installed ubuntu 9.04 server edition and all the servers i needed on it. everything worked just fine until the power supply and the motherboard blew up and i had to get another computer.
Now on this other computer (which i just moved my hard drive to) ubuntu loads fine but does not know that computers have changed and that i probably have a different network driver now (at least that's my guess as to why there's no network anymore)
So anyway, here's what i know about my system and i hope some1 can help me:

i have a g41m4l motherboard, after a look at the site i discovered that the onboard network card is realtek 8103EL

ifconfig returns 2 entries (localhost and virtual something, i think), no ETH0

lspci show me that i have REALTEK 8101E/8102E, which is close enuf, i guess :)

lsmod doesn't show me anything that looks like anything to do with the network card (at least the name) but there is a suspicious line that reads "r8169" and then a line after it that reads "mii" and is used by "r8169"

so i tried sudo modprobe r8169 but nothing much happens

I hope i don't sound completly dumb (since frankly, i have no idea what lsmod and modprobe actually do, i just picked it up from other forums). can any1 help?

---

