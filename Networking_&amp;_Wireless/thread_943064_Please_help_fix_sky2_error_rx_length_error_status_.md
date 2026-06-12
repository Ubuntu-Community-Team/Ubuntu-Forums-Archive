---
title: "Please help fix: sky2 error: rx length error: status 0x42c0500 length 600"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by trapix22 on 2008-10-09
-Installation on Toshiba Satellite laptop with Marvel Technologies NIC (88E8039)
- sky2 module is loaded
- "lspci" shows all NIC details - so the card is recognized

As soon as I log into console, I get repeated, continuously running error: **sky2 eth0 error: rx length error: status 0x42c0500 length 600** - it fills the screen and keeps running over and over.

When I do: ifconfig eth0 down -> it stops. When I bring it back up... It starts again.

- On my PC, with just a generic NIC card - THERE IS NO ERROR.

I've tried it with Linux Mint, DSL and Slackware and NONE of those show the error. It seems to be a kernel issue. I'd prefer not to have to change distros for this one error but it's making my terminal unusable.

I've exhausted all search avenues and I'm hoping someone can give me direction - at least to narrow down what to look for.
Thank you.

---

### Post by trapix22 on 2008-10-25
Well... This didn't fix the error... Lots of people with this problem... no solution yet. So I went and bought a USB / Ethernet adapter for $9.99, plugged it into USB port, installed my system without any errors at all. It definitely points to a problem with the Marvell Yukon NIC. Hope this temp fix helps someone.

---

### Post by skyraven on 2009-04-03
and to help you think in an optimistic way...the bug is still present now in April 2009...
I get it on my home pc..but thinking in a good way..maybe the easter bunny brings a fix:)

Edit:

Decreasing MTU to 1492 on those net cards seems to remove those messages forever..

---

