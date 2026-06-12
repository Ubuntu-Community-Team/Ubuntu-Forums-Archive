---
title: "Overly cautious Ubutu wireless connectivity"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by MrMercutio on 2008-06-26
Let me first describe our situation. We're two neighbours with two cabins far out in the swedish woods, and we have up to now shared an ADSL internet connection using the telephone line that's in my cabin. We're miles away from other neighbours, so we have decided that that in order to easily share connection, we both have wireless and my router is completely open. No protection what so ever.

Both of us have installed Ubuntu 8.04. My neighbour because I got tired of coming to the rescue over various windows problems on his ageing laptop. Now, however, neither of us can connect to the router.

The reason for this is that Ubuntu refuses to recognize that our router does not have any encryption or login. It requests a WPA1 password. We have of course gone over the setup of the router, and we have changed router, but the problem persists. I'm quite stumped actually.

It seems that Ubuntu can not recognize an unprotected router, and insists that there is WPA protection. Now, the easy solution is, of course, to set up the router with a WPA login, but basically that's just asking for trouble since connectivity can sometimes be problematic. My neighbour is not the least computer savvy, and I just want to spare myself hours of "internet support" when I'm at the cabin to lie in the grass in the sunshine.

Cheers,
MrMercutio

---

### Post by kevdog on 2008-06-26
Can you post the results of:

lshw -C network
ifconfig
iwlist scan

---

