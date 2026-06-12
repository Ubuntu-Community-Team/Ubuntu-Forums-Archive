---
title: "Internet doesn't want to work."
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by Aryiam on 2007-01-17
Hey!

I seem to have a problem I can't resolve, so all your opinions on this matter. I have ubuntu 6.10 and all seems to be fine. I've configured the network and everything is perfect (I tried to ping a few computers from my network and it worked).

The thing is I had to change my MAC address in order to make the internet work, and I did, with these commands:

sudo ifconfig <device> *(eth0 for me)* down
sudo ifconfig <device> hw ether <address>
sudo ifconfig <device> up

Good, in theory all should be okay now, but uhh, it's not! I don't seem to understand why it doesn't work... any ideas, suggestions?

Thanks in advance,
Antonio S.

PS - Oh, and since I'm new around here, hey all!

:KS

---

